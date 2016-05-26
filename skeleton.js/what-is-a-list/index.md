# What is a collection?

Backbone collections are simply an ordered set of [models](/what-is-a-model).   Such that it can be used in situations such as;

* Model: Student, Collection: ClassStudents
* Model: Todo Item, Collection: Todo List
* Model: Animal, Collection: Zoo

Typically your collection will only use one type of model but models themselves are not limited to a type of collection;

* Model: Student, Collection: Gym Class
* Model: Student, Collection: Art Class
* Model: Student, Collection: English Class

Here is a generic Model/Collection example.

```js

var Song = Backbone.Model.extend({
    initialize: function(){
        console.log("Music is the answer");
    }
});

var Album = Backbone.Collection.extend({
    model: Song
});

```

## Building a collection

Now we are going to populate a collection with some useful data.

```js

var Song = Backbone.Model.extend({
  defaults: {
    name: "Not specified",
    artist: "Not specified"
  },
  initialize: function(){
      console.log("Music is the answer");
  }
});

var Album = Backbone.Collection.extend({
  model: Song
});

var song1 = new Song({ name: "How Bizarre", artist: "OMC" });
var song2 = new Song({ name: "Sexual Healing", artist: "Marvin Gaye" });
var song3 = new Song({ name: "Talk It Over In Bed", artist: "OMC" });

var myAlbum = new Album([ song1, song2, song3]);
console.log( myAlbum.models ); // [song1, song2, song3]

```