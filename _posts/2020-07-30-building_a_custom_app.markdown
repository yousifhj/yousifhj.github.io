---
layout: post
title:      "Building a custom App "
date:       2020-07-30 17:31:36 +0000
permalink:  building_a_custom_app
---


In this blog, I will go over a few things that were crucial in creating my application. I was asked to build a custom app which can track information important to a user. For this project I decided to create a simplified plant organization application that allows users to add in and keep track of users plants.

I started off by adding use Rack::MethodOverride to the config.ru file. This adds Sinatra middleware which allows me to send HTTP, Patch and Delete requests.

The first thing I did was create a database with a Plant table as well as a Users table that way I can store the data.

rake db:create_migration NAME=create_plants
rake db:create_migration NAME=create_users

The create_plants.rb and create_users.rb file has the following code:

class CreatePlants <ActiveRecord::Migration
  def change
    create_table :plants do |t|
      t.string :name
      t.integer :price
      t.string :water
      t.string :light
      t.string :notes
      t.integer :user_id
    end 
  end 
end 

class CreateUsers <ActiveRecord::Migration
  def change
    create_table :plants do |t|
      t.string :username
      t.string :email
      t.string :password
    end 
  end 
end

I ran rake db:migrate to create the migration. I then created the matching Plants and User class that would inherit from ActiveRecord::Base

class Plant < ActiveRecord::Base
  belongs_to :user
end
class User < ActiveRecord::Base
  has_many :plants
end

The database and model are set up. I now can implement CRUD.

###CREATE

The first thing I need to do to create a plant is to create a HTTP get request that renders a new.erb view.

get '/plants/new' do
  erb :'plants/new'
end

My new.erb views contains the following:

<h2> Add a Plant: </h2>
  <form method="POST" action="/plants">
    <label for="name">Name:</label>
    <input type="text" name="name">
    <label for="Water">Water:</label>
    <input type="text" name="water">
    <label for="light">Light:</label>
    <input type="text" name="light"> 
    <label for="price">Price:</label>
    <input type="integer" name="price">
    <label for="notes">Notes</label>  <br>
    <textarea type="text" name="notes"></textarea><br>
    <input type="submit">
 </form>
 
The form posts the ‘/plants’ route where a new plant is instantiated with user data which then gets redirected to ‘/plants’.

post '/plants' do
   if  params[:name] == "" || params[:water] == ""  ||   params[:light] == "" || params[:price] == ""  || params[:notes] == ""
   redirect '/plants/new'
end

plant = current_user.plants.build(name: params[:name],water: params[:water], light: params[:light], price: params[:price], notes: params[:notes], user_id: current_user.id)
   if plant.save
       redirect '/plants'
   else
       redirect '/plants/new'
   end
end

###READ

Now that a plant is created I can now implement the two reader requests. First I would index all the plants. This request stores all instances of plants inside the instance variable @plants and renders the index view.

get '/plants' do  
   if logged_in?
      user = current_user
      @plants = user.plants
      erb :'plants/index
   else
      redirect "/login"
   end 
end 

In the index view, I iterate over the plants array and for each plant, I output the Plant name.

<% @plants.each do |p| %>
    <p><a href="/plants/<%= p.id %>"><%= p.name %></a></p>
<% end %>

I can also read a specific plant using using dynamic route and ActiveRecord’s find method.

get '/plants/:id' do
  if logged_in?
    user = current_user
    @plant = user.plants.find_by(id: params[:id])
    if @plant
      erb :'plants/show'
    else
      redirect '/plants'
    end
  else
    redirect "/login"
  end
end

The show view would then output the following information about each plant.

<p>Plant Name: <%= @plant.name%></p>
<p>Water: <%= @plant.water%></p>
<p>Light: <%= @plant.light%></p>
<p>Price: <%= @plant.price%></p>
<p>Notes: <%= @plant.notes%></p>

###UPDATE

To edit a specific plant, I would send a get request to ‘/plants/:id/edit’ which will use dynamic route to get user input and find the plant.

get '/plants/:id/edit' do
  if current_user
    @plant = current_user.plants.find_by(id: params[:id])
    erb :"plants/edit"
  else
    redirect "/login"
  end
end

The request then renders the form in edit.erb:

<form action="/plants/<%= @plant.id%>" method="POST">
<input type="hidden" id="hidden" name="_method" value="PATCH">
<h4>Name: <input type="text" name="name" value= "<%= @plant.name %>"></h4>
<h4>Water: <input type="text" name="water" value= "<%= @plant.water %>"></h4>
<h4>Light: <input type="text" name="light" value= "<%= @plant.light %>"></h4>
<h4>Price: <input type="integer" name="price" value= "<%= @plant.price %>"></h4>
<h4>Notes: <input type="text" name="notes" value= "<%= @plant.notes %>"></h4>
<input type="submit" name="submit" value="Update Plant">

The form sends all the user input to the patch request ‘/plants/ <%=@plant.id%>’.
The patch request finds the plant and updates it with the new user input and redirects to the specific plant using the plant_id.

patch '/plants/:id' do
  @user = current_user
  @plants = @user.plants.find_by(id: params[:id])
  if !@user
    redirect '/login'
  else
    @plants.update(name: params[:name],water: params[:water], light: params[:light], price: params[:price], notes: params[:notes])
    redirect "/plants/#{@plants.id}"
  end
end

DELETE
To delete a specific plant I added in a delete button in show.erb. This from will send a request to ‘delete “/plants<%=plant.id%>”’.

<form method="POST" action="/plants/<%= @plant.id %>">
  <input type="hidden" name="_method" value="DELETE">
  <input type="submit" value="Delete Plant">
</form>

In the delete route I find the plant using “current_user.plants.find_by(id: params[:id])” and delete it with the destroy method and redirect to ‘/plants’ that way user is able to see the remaining plants in the data base.

delete '/plants/:id' do
  if !logged_in?
    redirect '/'
  else @plant = current_user.plants.find_by(id: params[:id])
    @plant.destroy
    redirect '/plants'
  end
end

I had so much fun creating this application. Once I completed all the requirements I went in and added some CSS to make it a little more appealing to the eye.

