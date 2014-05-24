<aside class="notes"></aside>
# Introduction to Meteor

## 2014-05-25



<aside class="notes"></aside>
# What is Meteor?



## What is Meteor?
<aside class="notes"></aside>

* Javascript web app framework
* Run on [node.js](http://nodejs.org/)
* [mongoDB](http://www.mongodb.org/)
* [Handlebars](http://handlebarsjs.com/)
* Data binding between client and server thru HTML5 web socket API
* Smart Package



## Installation
<aside class="notes"></aside>

Linux - [Meteor official site](https://www.meteor.com)

Windows - [Meteor on Windows!](http://win.meteor.com/)



## Scafold a Meteor project
<aside class="notes"></aside>

```
meteor create ykyuen
```



## Basic file structure
<aside class="notes"></aside>

* .meteor
  * .gitignore
  * packages - List of meteor packages associated with this project
  * release - Meteor version
* ykyuen.css - CSS file
* ykyuen.html - Handlebars template
* ykyuen.js - Server and clent side javascript



## Start the node.js server
<aside class="notes"></aside>

```
meteor
```

The Meteor app is available @ http://localhost:3000



## Meteor watch
<aside class="notes"></aside>
Try to make some changes on the .html, .css or .js without stopping the node.js server. The app will autoreload for the changes.



The Handlebars template
<aside class="notes"></aside>

```
<head>
  <title>ykyuen</title>
</head>

<body>
  {{> hello}}
</body>

<template name="hello">
  <h1>Hello ykyuen!</h1>
  {{greeting}}
  <input type="button" value="Click" />
</template>

```



## The server and client side js
<aside class="notes"></aside>

```
if (Meteor.isClient) {
  Template.hello.greeting = function () {
    return "Welcome to ykyuen.";
  };

  Template.hello.events({
    'click input': function () {
      // template data, if any, is available in 'this'
      if (typeof console !== 'undefined') {
        console.log("You pressed the button");
      }
    }
  });
}

if (Meteor.isServer) {
  Meteor.startup(function () {
    // code to run on server at startup
  });
}
```



## The Meteor packages
<aside class="notes"></aside>

```
meteor list
```

```
meteor add bootstrap
```

```
meteor remove bootstrap
```



## The Meteor packages
<aside class="notes"></aside>

There are not many standard packages available!?

Ans: You can include the libraries manually.

OR

[Meteorite](https://github.com/oortcloud/meteorite/) - Meteor version manager and package manager

Checkout the available meteor packages @ [Atmosphere](https://atmospherejs.com/)



## mongoDB
<aside class="notes"></aside>

Let's create a collection in the app bundled mongodb.

Login to the local app mongodb:
```
mongo 127.0.0.1:3001/meteor
```



## mongoDB
<aside class="notes"></aside>

Let's create a collection:
```
db.createCollection("fruits");
```



## mongoDB
<aside class="notes"></aside>

Add some fruits:
```
db.fruits.insert([
  { _id: 1, name: "Apple"},
  { _id: 2, name: "Orange"},
  { _id: 3, name: "Pear"},
  { _id: 4, name: "Banana"}
]);
```



## mongoDB
<aside class="notes"></aside>

List the inserted fruits:
```
db.fruits.find();
```



## mongoDB
<aside class="notes"></aside>

You can connect to remote mongodb server by setting the following environmental variable before you start the meteor app.
```
MONGO_URL = "mongodb://<username>:<password>@<endpoint>"
```



## Databinding in Meteor
<aside class="notes"></aside>

Create a new template for listing the fruits:
```
<body>
  {{> hello}}
  {{> fruitList}}
</body>
<!-- Omit the unrelated code -->
<template name="fruitList">
  <ul>
    {{#each fruits}}
      <li>{{name}}</li>
    {{/each}}
  </ul>
</template>
```



## Databinding in Meteor
<aside class="notes"></aside>

Add the Model at the top of the ykyuen.js:
```
// Models
FruitsCollection = new Meteor.Collection('fruits');
```

Implement the template logic in the client side js:
```
// Template: fruitList
Template.fruitList.fruits = function () {
  var fruits = FruitsCollection.find({});
  return fruits;
};
```



## Databinding in Meteor
<aside class="notes"></aside>

Keep looking at your browser window and insert a new fruit thru the mongodb client:
```
db.fruits.insert({ _id: 5, name: "Strawberry"});
```

Then remove it:
```
db.fruits.remove({ _id: 5});
```

The binding is done by html5 web socket API and all the clients will received the changes.



## A more complete Meteor file structure
<aside class="notes"></aside>

* client/
  * js/
    * _Client side JS files_
  * css/
    * _Stylesheets_
  * compatibility/
    * _JS flies without wrapped in a new variable scope and executed after the client/*.js_
* server/
  * server.js
    * _The server side js_



## A more complete Meteor file structure
<aside class="notes"></aside>

* private/
  * _Any files which are only accessible on server side_
* public/
  * _Public folder for web assets such as images and fonts_
* model.js
  * _Database models_