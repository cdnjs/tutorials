# React/Redux beginners tutorial (one file)

I struggled learning the React/Redux world so I thought that I should write a simple tutorial in case there are others like me. By the end of this tutorial you should have a runnable app that is all contained in one `index.html`. (You don't need to know gulp, grunt, burp etc)

## Why is Redux with React a good idea?

**React** is a UI framework that renders the same output predictably when given state.

**Redux** is a predictable state container.

    ... Redux works especially well with frameworks like React and Deku because they let you describe UI as a function of state, and Redux emits state updates in response to actions

## What you will learn

How to make React components update when given state by Redux via action creators and reducers.

[Tutorial Demo](http://thomasdavis.github.io/react-redux-tutorials/) (Make sure you install [Redux DevTools]()!)

[Tutorial Code](https://github.com/thomasdavis/react-redux-tutorials) (The whole tutorial is contained in one file!)

I didn't write the best code I could and instead opted to write it in such a way that one could just "get" it. If this is too simple for you or once you finish it, make sure you read [Full-Stack Redux](http://teropa.info/blog/2015/09/10/full-stack-redux-tutorial.html) by Tero Parviainen.

It goes without saying that the tutorials by the creator of Redux are [also amazing](https://egghead.io/series/getting-started-with-redux). (Uses React in some of the examples)

## Getting started

First checkout the example, then scan over the `index.html` in the repo. I am just going to cover each section as opposed to writing copy and paste steps.

**Let's start by importing the scripts and variables we need**

(This looks much nicer when properly built with something like Webpack)

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.11.2/lodash.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/redux/3.5.2/redux.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.0.1/react.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.0.1/react-with-addons.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react-redux/4.4.5/react-redux.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js" type="text/javascript"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.0.1/react-dom.js" type="text/javascript"></script>

<script type="text/babel">

  const {connect, Provider} = ReactRedux; // import {connect, Provider} from 'react-redux';
  const {createStore, compose} = Redux; // import {createStore} from 'redux';
  const {Component} = React; // import {Component} from 'react';
  const {map} = _; // import {map} from 'lodash'

</script>
```

So we are importing variables from these npm packages;

* redux
* react
* react-redux (Connects redux and react together)
* babel (let's us write ES6 in script tags, transpiles on the fly)
* react-dom (Let's us render the React components to the page)

## Overview

Basically Redux exposes a publish and subscribe API for the `store`/`state` it creates. Though those words won't get you very far and you will very quickly use the terms Action Creators and Reducers.

React and Redux don't directly communicate, and instead just work with the state of the application.

1. Redux creates a store/state.
2. Redux then creates `reducers` (listeners) that listen for actions (events)
3. React components can dispatch (publish) these events via `store.dispatch`
4. Redux then reduced (recalculated) state based off the dispatched action and returns a new copy of state. (State is immutable, it never changes, so we end up a history of state over time)
5. Once state has been reduced, React is free to re-render based off the new state.


    A store holds the whole state tree of your application.
    The only way to change the state inside it is to dispatch an action on it. [1]

## React component

Here we define our React component for the tutorial, as you can see there is nothing magical about it at this point. (It could actually be split up much more logically but one component for the tutorial will reduce complexity)

A lot of the explanations can be found in the code comments below.

```js
class ListTable extends Component {
  constructor (props, context) {
    // We use the constructor to make sure our eventHandlers know of `this`
    // Otherwise they will inherit the normal event arguments
    super(props, context);
    this.addItem = this.addItem.bind(this);
    this.removeItem = this.removeItem.bind(this);
    this.editItem = this.editItem.bind(this);
  }

  // These event handlers (react) will be responsible for dispatching (redux) our action creators (redux)
  addItem () {
  }
  removeItem (index) {
  }
  editItem (index, event)  {
  }


  render () {
    // ES6 desconstruct some constants from our props
    // Short hand syntax for saying `const items = this.props.items`
    const {items, addItem} = this.props;

    // Here we essentially just want to loop over our `items` and render the appropiate html
    // Not too much going on, just take note of the `onChange` and `onClick` which
    // call the handlers above
    return (<div>
      <table>
        <tbody>
          {map(items, (item, index) => {
            return (<tr key={index}>
              <td><input onChange={this.editItem.bind(null, index)} type="text" value={item} /></td>
              <td>
                <button onClick={this.removeItem.bind(null, index)} className="delete">
                  <i className="fa fa-trash"></i>
                </button>
              </td>
            </tr>);
          })}
        </tbody>
      </table>
      <button onClick={this.addItem} className="add">
        <i className="fa fa-plus"></i>
      </button>
      <InfoBox />
    </div>);
  }
}
```
## Set up the react component

## Connect redux

## setup the action dispatchers, log the stuff

## Create the reducers

## References

[1] http://redux.js.org/docs/api/Store.html

- Attributes are camelcase
- JSX will validate your HTML as you go
- state is immutable, it never changes, you have to recreate a new one
