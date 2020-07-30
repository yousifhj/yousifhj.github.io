---
layout: post
title:      "DashOfDelish Rails Project"
date:       2020-07-30 17:35:59 +0000
permalink:  dashofdelish_rails_project
---


For my third project I have decided to create a Recipe App called DashOfDelish where bakers and cooks can keep track of their recipes. This App was built using Ruby on Rails and no scaffolding was used to build this project.

###Creating the Application

*$ rails new DashOfDelish*

###Required Gems

gem 'devise'
gem 'omniauth-github' 
gem 'pry'
gem 'dotenv-rails'

###Database

My project has a few tables, below is the recipe’s table.

Image for post
Recipe’s Table

###Models

The model supoports the connection between the object and the database. It also takes care of the validation, association and transactions. For this project I have 4 models; application_record category, recipe and user. Below is my Recipe Model.

I have added validations to ensure that a recipe has a title, description, directions and ingredients. I’ve also used the scope method to allow the user to search for a specific recipe.

Image for post

###Views

This is where all the magic happens. This is where the user sees and interacts with the app. It’s a narration of data in a specific format. Views are prompted by a controller’s decisions to represent the data.

###Controller

The controller stores all of the information. It takes care of the flow. It uses models to do queries, parses data, and make decisions about what setup you’ll present the data. My recipes controller also uses flash, which is provided by rails. It provides the user with information about creating a recipe.

Image for post
MVS were set up, Now for the fun stuff!

###Scope Method

While working on my project I definitely had questions here and there. One of the concepts that was hard for me to understand was the scope method. Once my project was running and everything worked as it should I didn’t know how to implement scope into my project. At first thought I thought about allowing the user to search through categories and allow the user to select from the recipes that were in the category but figured it would be more helpful users are able to search a specific word to find the related recipe.

Implementing this method allows users to find recipes that, for example, have the word “cake” in the title.

Once my project was complete I was able to add in CSS with the help of the bootstrap gem. It all came together beautifully. I’m super proud!


Hope this helped :)
