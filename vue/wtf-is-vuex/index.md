Vuex. Is it pronounced “vewks”, or “veweks”? Or maybe it’s meant to be “vew”, pronounced with a French-style silent “x”?

My trouble with understanding Vuex only began with the name.

Being an eager Vue developer I’d heard enough about Vuex to suspect that it must be an important part of the Vue ecosystem, even if I didn’t know what it actually was.

I eventually had enough of wondering, so I went to the documentation with plans of a brief skim through; just enough to get the idea.

To my chagrin I was greeted with unfamiliar terms like “state management pattern”, “global singleton” and “source of truth”. These terms may make sense to anyone already familiar with the concept, but for me they didn’t gel at all.

The one thing I did get, though, was that Vuex had something to do with Flux and Redux. I didn’t know what those were either, but I figured it may help if I investigated them first.

After a bit of research and persistence the concepts behind the jargon finally started to materialise in my mind. I was getting it. I went back to the Vuex documentation and it finally hit me…Vuex is freaking awesome!

I’m still not quite sure how to pronounce it, but Vuex has become an essential piece in my Vue.js toolbelt. I think it’s totally worth your time to check it out too, so I’ve written this primer on Vuex to give you the background that I wish I’d had.

Note: This article was originally posted [here on the Vue.js Developers blog](http://vuejsdevelopers.com/2017/05/15/vue-js-what-is-vuex/?jsdojo_id=cjs_wfv) on 2017/05/15.

## Understanding The Problem That Vuex Solves

To understand Vuex it’s much easier if you first understand the problem that it’s designed to solve.

Imagine you’ve developed a multi-user chat app. The interface has a user list, private chat windows, an inbox with chat history and a notification bar to inform users of unread messages from other users they aren’t currently viewing.

Millions of users are chatting to millions of other users through your app on a daily basis. However there are complaints about an annoying problem: the notification bar will occasionally give false notifications. A user will be notified of a new unread message, but when they check to see what it is it’s just a message they’ve already seen.

What I’ve described is a real scenario that the Facebook developers had with their chat system a few years back. The process of solving this inspired their developers to create an application architecture they named “Flux”. Flux forms the basis of Vuex, Redux and other similar libraries.

## Flux

Facebook developers struggled with the “zombie notification” bug for some time. They eventually realised that its persistent nature was more than a simple bug; it pointed to some underlying flaw in the architecture of the app.

The flaw is most easily understood in the abstract: when you have multiple components in an application that share data, the complexity of their interconnections will increase to a point where the state of the data is no longer predictable or understandable. Consequentially the app becomes impossible to extend or maintain.

The idea of Flux was to create a set of guiding principles that describe a scalable front end architecture that sufficiently mitigates this flaw. Not just for a chat app, but in any complex UI app with components and shared data state.

Flux is a pattern, not a library.

You can’t go to Github and download Flux. It’s a design pattern like MVC. Libraries like Vuex and Redux implement the Flux pattern the same way that other frameworks implement the MVC pattern.

In fact Vuex doesn’t implement all of Flux, just a subset. Don’t worry about that just now though, let’s instead focus on understanding the key principles that it does observe.

## Principle #1: Single Source of Truth

Components may have local data that only they need to know about. For example, the position of the scroll bar in the user list component is probably of no interest to other components.

But any data that is to be shared between components, i.e. application data, needs to be kept in a single place, separate from the components that use it.
This single location is called the “store”. Components must read application data from this location and not keep their own copy to prevent conflict or disagreement.

```js
// Instantiate our Vuex store
const store = new Vuex.Store({
  
  // "State" is the application data your components
  // will subscribe to
  
  state: {     
    myValue: 0   
  }
});
// Components access state from their computed properties
const MyComponent = {   
  template: `<div>{{ myValue }}</div>`,
  computed: {
    myValue () {
      return store.state.myValue;
    }   
  } 
};
```

## Principle #2: Data is Read-Only

Components can freely read data from the store. But they cannot change data in the store, at least not directly.

Instead they must inform the store of their intent to change the data and the store will be responsible for making those changes via a set of defined functions called “mutations”.

Why this approach? If we centralise the data-altering logic than we don’t have to look far if there are inconsistencies in the state. We’re minimising the possibility that some random component (possibly in a third party module) has changed the data in an unexpected fashion.

```js
const store = new Vuex.Store({ 
  state: { 
    myValue: 0
  }, 
  mutations: { 
    increment (state, value) { 
      state.myValue += value;
    }
  } 
});
// Need to update a value?
// Wrong! Don't directly change a store value.
store.myValue += 10;
// Right! Call the appropriate mutation.
store.commit('increment', 10);
```

## Principle #3: Mutations Are Synchronous

It’s much easier to debug data inconsistencies in an app that implements the above two principles in it’s architecture. You could log commits and observe how the state changes in response (which you can indeed do when using Vuex with Vue Devtools).

But this ability would be undermined if our mutations were applied asynchronously. We’d know the order our commits came in, but we would not know the order in which our components committed them.

Synchronous mutations ensure state is not dependent on the sequence and timing of unpredictable events.

## Finally: What is Vuex?

With all that background out of the we are finally able to address this question.
Vuex is a library that helps you implement the Flux architecture in your Vue app. By enforcing the principles described above, Vuex keeps your application data in a transparent and predictable state even when that data is being shared across multiple components.

Its implementation includes a store, custom mutators and it will reactively update any components that are reading data from the store.

It also allows for cool development features like hot module reloading (updating modules in a running application) and time travel debugging (stepping back though mutations to trace bugs).

Sound cool. I have some questions…

Maybe you’re wondering now whether or not your app needs Vuex, how it integrates with vue-devtools or how you can commit data from asynchronous functions.

My goal in this article was just to give you a primer on Vuex. I hope you’ll find if you go to the documentation now, you’ll feel well equiped to get these answers yourself.

*Get the latest Vue.js articles, tutorials and cool projects in your inbox with the [Vue.js Developers Newsletter](http://vuejsdevelopers.com/newsletter/?jsdojo_id=cjs_wfv).*
