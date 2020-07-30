---
layout: post
title:      "React and Redux"
date:       2020-07-30 17:44:57 +0000
permalink:  react_and_redux
---


Below are a few things I’ve picked up since studying React and Redux.React and Redux are very good matches when they work together but only by understating them individually we can work them together.

## REACT
### Components

There are two types of components in React. There are class components and functional components. Class components hold state and use lifecycle methods. Functional components are stateless components.

### Container Presentation Pattern

Container components worry about how things act or how things work for the components. They provide data to presentation components. Presentation components only worry about how things look. They just have a render method with no other logic and are stateless.

### JSX
JSX is the syntax that is used to build a react component. It’s similar to HTML when it comes to building your react component. It is an XML syntax for component building.

### Stateful Components

A stateful component is dependent on it’s state object and it can change it’s own state. The component re-renders based on changes to it’s state, and may pass down properties of it’s state to child components as properties on a props object. Stateful components have internal state.

### Lifecycle method

These are the methods used for a particular component. The first thing that can be used is component willMount. This is referring to when the component will be rendered to the screen. Once it is rendered you can say the component didMount. This is saying the component has been rendered. The next component will unMount.This means the component will be destroyed.

### Local State

When we think about local state in react we want to think about states that live inside the components. Local states in components would be managing the UI of a particular component. any presentational attribute would be handled by state.

### State Flow

In react sate flows from parent component to child component. It is a downward motion. When state is needed in a child component it is passed to it by it’s parent via prop.

### Props

Props are what is passed from the patent to the child. This is how you can access state from your parent component. One thing to note about props is that it can’t be modified. If there is a change that needs to be made it would have to happen in the parent component.

### Stateful Components

Stateful components are components that have their own state and they use lifecycle methods. Lifecycle methods are used for the component to be rendered to the DOM.

## REDUX
### Actions

Actions are events. Actions send data from an application to the store.The store gets the information only from actions. Internal actions are simple JavaScript objects. They have a type property, describing the type of action and payload of information being sent to the store.

### Store

The entire state is represented by a single store. That makes Redux simple and foreseeable. Any action returns a new state via reducers. Store is the object that holds the application state and provides a few helper methods to access the state, dispatch actions and register listeners.
