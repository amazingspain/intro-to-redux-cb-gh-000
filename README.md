# Introduction to React + Redux

## Objectives

* Gain a basic understanding of Redux architecture 
* Understand the difference between declarative and imperative programming
* Understand how Redux helps make React apps more declarative


## Introduction: Managing Application State

We already know that React is a view-layer framework that provides a way for us developers to present changeable, reactive views to our users. In order to track and enact the appropriate changes to the view that a user is interacting with, we have the concept of *state*. 

What do we mean by "state"? Think of state as the sum of all the information that describes your application at a given point in time. It could include data pulled from your back-end API and data describing the UI. For example, imagine a shopping list application. The state at a certain moment would include the shopping list items that the user has created, the knowledge of which shopping list items have been crossed out or checked off, the knowledge of which shopping list a user is current viewing, etc. 

State will frequently change depending on a user's interaction with our app (for example a user adds a new shopping list item or clicks a tab that hides the list they were viewing to display a different list) or if new data is pulled from the backend API. What a user actually sees and interacts with at a given point in time is really the reflection of the state of the application at that point in time. 

So, if an app is really the sum or reflection of its current state, and if that state must be capable of changing, then we as developers need to be able to teach our applications how to manage their own state.

The Redux framework allows us to do just that. Redux is a centralized state management system. This means that, instead of having individual components be responsible for their own state, we will maintain one application state which will be emitted or passed down to all of our components. 

Here's the basic flow:

![](https://s3-us-west-2.amazonaws.com/curriculum-content/web-development/react/react-diagram.png)

What's so great about this?

Redux abstracts away our components' interactions with the store, instead managing state through the interaction between components, actions and reducers. This makes our code more **declarative** and less **imperative**. 

### Declarative vs. Imperative Programming

Declarative code is code that tells our program *what* to do, not *how* to do it. For example, if we wanted to iterate over a collection and `console.log` each member of the collection, we could imperatively write:

```javascript
for (i = 0; i <= array.length; i++) {
  console.log(array[i])
}
``` 

This code explicitly tells our program how to iterate with the complex set of instructions given to our `for` loop. 

We could clean this up significantly by taking a declarative approach:

```javascript
array.forEach((el) => {console.log(el)})
```

We didn't tell our program *how* to iterate, we just told it *what* to do, using the `forEach` function. 

Redux provides a similar degree of abstraction to our React architecture by providing us with a set of functions for managing application state. Let's take a closer look. 

## Redux Architecture

With Redux, our application state is centralized and managed by a single store––not by individual components. A component's properties should be considered immutable. Instead of a component responding to a user's action by updating it's own properties, it will send an action that updates the entire application's state, which in turn triggers a re-render of a component, updating that component's properties (and what a user sees/interacts with) as a result.

How does Redux manage all this? With the help of the store, the actions and the reducers.

Let's go through a quick refresher:

### Actions

Actions are JSON objects that contain information about changes that need to be made to state. They can be dispatched by various parts of your application, and they are received by the store.

Actions are produced by functions called action creators.

### Store

The store holds the whole state our application. It can dispatch actions and it receives actions that are dispatched to it. However, the store doesn't want to handle the dispatched actions and actually enact changes to state. For that, we use reducers.

### Reducers

The store passes dispatched actions to reducers, which receive the actions and make the appropriate changes to state.

### Components

Components are the presentation, or view, layer of our application. Certain components, the parent or container components, will be connected to our store. Those components will be alerted whenever a change to state has been made by a reducer. Those components will then re-render, with new properties as dictated by the changes made to application state.

 
### React + Redux Components and The Store

It is important to note that in Redux, **components do not directly interact with the store**. Redux instead introduces a layer of abstraction between the components and the store by providing us with some functions that connect our components to the store. This allows us to dispatch actions directly from within these components, without having to call `store.dispatch(someAction())` *and* it allows these components to automatically re-render when application state has changed. 

## Coming Up...

Now that we have a basic understanding of the architecture of Redux and the tools that Redux provides, let's build something!

















