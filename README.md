# Vue.js:  Getting Started

A repo to contain notes code examples from the Vue.js Getting Started course on PluralSight

## Module 1:  Introducing Vue.js

### Benefits

* Simplicity
* Speed
* Easy to learn
* Easy to develop with
* Easy to maintain
* Fast

#### Simplicity

##### Templates

* Allows for separation between UI and Data and Business Logic
* Minimizes the amount of code you write; avoid dupliated/redundant HTML
* Protect you from changes; make changes to the UI in one place

##### Declaritive Binding

* The "glue" that holds the UI and data together
* Simplify development; separation of concerns between UI and data/business logic
* Remove the burden of managing the DOM
* Updates occur automatically

Template Example with Declaritive Bindings:

```HTML

<div v-for="beer in beers">
    <div>
        <h5>{{beer.name}}</h5>
        <small style="color:gray">
            abv: {{beer.abv}}
        </small>
    </div>
</div>

```

Data being used in Template:

```JavaScript

beers: [
    { name: 'Ahool Ale', abv: 5.4 },
    { name: 'Sigbin Stout', abv: 8.1 }
]

```

#### Speed

* Starts and runs fast:
  * Small library size and Virtual DOM
    * 27.3kb (gzipped) - 74.8kb
    * Virtual DOM
      * Lightweight copy of actual DOM
      * Allows for efficient determination of what needs to be updated
      * Batches updates

#### Other Considerations

* Browser Support
* Licensing

##### Browser Support

* Legacy Browsers - IE9+
  * React doesn't support IE below 11
* Evergreen Browsers - Chrome, Edge, Firefox, and Safari
* Mobile Browsers - Android, Safari on iOS

#### Licensing

* MIT Licensing
  * Also used by jQuery and Angular
  * ~~React uses 3-clause BSD license with Facebook Addendum~~
  * As of September 2017, React now also uses MIT Licensing

#### Installing & Setting up Vue.js

* Install Vue.js
* Install Axios (Ajax)

Install Vue.js

* Core library
* Available via CDN
* unpkg is recommended
* Can use package manager to obtain Vue.js as well

```HTML

https://unpkg.com/vue

```

Install Axios

* Library used for making Ajax calls

```HTML

https://unpkg.com/axios/dist/axios.min.js

```

Example Vue.js Application with references to Vue and Axios:

```HTML

<html>
    <head>
        <title>Growler</title>
    </head>
    <body>
        <div id="growler">
            <script type="text/javascript" src="https://unpkg.com/vue"></script>
            <script type="text/javascript" src="https://unpkg.com/axios/dist/axios.min.js"></script>
        </div>
    </body>
</html>

```

#### Initialize an Instance of Vue

```JavaScript

//Constructor for a Vue App
var growler = new Vue ({
    el: '#growler',
    data: {

    }
});

```

#### Mounting an Instance of Vue - 2 options

Option 1: JavaScript:

```JavaScript

...
el: document.getElementById('growler')
...

```

Option 2: CSS Selector (recommended):

```JavaScript

...
el: '#growler'
...

```

#### Lifecycle of a View

1. Creation
    * beforeCreate
    * created
1. Mounting
    * beforeMount
    * mounted
1. Updating
    * beforeUpdate
    * updated
1. Destroy
    * beforeDestroy
    * destroyed

#### Creation Stage

1. beforeCreate hook fires
1. {custom logic fires here}
1. Initialize State occurs
1. created hook fires

* Compile Template

#### Mounting Stage

1. beforeMount hook fires
1. {custom logic fires here}
1. Create Virtual DOM
1. mounted hook fires

* Listen for Data Changes

#### Updating Stage

1. beforeUpdate hook fires
1. {custom logic fires here}
1. Re-Render Virtual DOM ("patches")
1. updated hook fires

#### Destroy Stage

1. beforeDestroy hook fires
1. Teardown Virtual DOM
1. destroyed hook fires

## Module 2:  Creating Vue.js Templates

### Accessing Data Property

In Vue.js, since the Data object defined in the Vue application is a POJO it can be accessed outside of the Vue Application.  Inside the Vue App, you can access the Data object in a short-handed way:

```JavaScript
growler.data.appName

//shorthand:
growler.appName
```

### Loading Data Properties

#### Data Property Caveats

* You can only modify properties
* You can't add or remove properties at runtime
* JavaScript objects are formatted differently
  * In order to examine the data easily, use ```vue-devtools``` plugin for Chrome

You can't do these things because the getters and setters are generated

#### Concepts

* Data serves as the "schema"

#### Loading a Property

Object.defineProperty is used to generate getters and setters during the Creation Stage

* Getters and Setters generated
* Enables Change Notifications
* Enables Dependency Tracking (?)

#### Enabling change notifications and dependency tracking is referred to as making the property "reative"

*QUESTION:  Is this data-binding?*

#### Naming Properties

* Needs to follow JavaScript naming rules
* Shouldn't start with $ or _

#### Property Values

* ```data``` property values should only be *data*
* Primitive values
* Do not use native objects; Number, String, Array, etc.

#### Binding Content to a Template

#### Binding Text - 2 Options

1. Semantic syntax
1. Declaritive syntax

#### Semantic Bindings

Double curly braces known as Mustaches!  {{...}}

```HTML

<h2>Welcome to {{ appName }}</h2>

```

#### Declaritive Bindings

* Created via directives
* All baked-in directives begin with "v-"

```v-text``` Directive:  Interpolates a property value as an HTML element's text

Example of using the v-text Directive:

```HTML

<h2 v-text="appName"></h2>

```

NOTE:  If you need to bind to *only* part of an element, use Semantic Binding!

#### One-Time Bindings

* ```v-once``` directive - renders the element once and only once
  * this includes Children
* Helps to optimize performance

```HTML

<h2 v-once>{{ appName }}</h2>

```

#### Binding to HTML (Elements)

* ```v-html``` directive - updates the innerHTML property
* Allows you to bind HTML (vs. text) to an element in your UI

```JS

var growler = new Vue({
    el: '#growler',
    data: {
        appName: '<a href="/">Growler</a>'
    }
});

```

```HTML

<h2 v-html="appName"></h2>

```

#### Binding to HTML Attributes

* ```v-bind``` directive - binds data property values to HTML attributes

#### Binding to CSS Classes

Allows us to maintain separation between the design (styles) and the data.

There are a few different options when binding to CSS Classes:

* Retrieve CSS Classes from an Object
* Retrieve CSS Classes from an Array (similar)
* Bind to specific CSS properties (interesting)

Retrieving CSS Classes from an Array:

```HTML

<h1 v-once v-text="appName" v-bind:class="[accentColor, headers]"></h1>

data () {
    return {
      ...      
      accentColor: 'accent-color',
      headers: 'headers',
      ...
    }
  }

<style scoped>
.accent-color {
  color:#FF6A00
}

.headers {
  font-family: 'Verdana';
  font-size: 3em;
  margin: 0;
}
</style>

```

Binding to specific CSS Properties:

```HTML

<h1 v-once v-text="appName" v-bind:class="{
      'headers': true,
      'accent-color': isOnline
    }"></h1>

data () {
    return {
        ...
        isOnline: true
        ...   
    }
  }    

<style scoped>
.accent-color {
  color:#FF6A00
}

.headers {
  font-family: 'Verdana';
  font-size: 3em;
  margin: 0;
}
</style>    

```

#### Using JavaScript Expressions

* A type of statement.
* A line of code that produces a value
* Expressions can be used with bindings
* Can be used in a Template
* Mustaches - {{}}
* Evaluated within the context of a view
* Executed within the Vue Sandbox - an isolated environment?
    * "Whitelisted" globals are available for use in this environment
    * See Whitelisted Globals slide from Vue.js Getting Started for reference

Expression being used in a Template:
```JS

var growler = new Vue({
    el: '#growler',
    data: {
        appName: 'Growler',
        isOnline: false
    }
});

```

```HTML

<h2
    v-text="appName"
    v-bind:style=
    "{ color:isOnline? '#FF6A00':'#000' }">
</h2>

```

## Module 3:  Binding with Forms in Vue.js

v-model directive - This can be used with:
* Text fields
* Checkboxes
* Radio buttons
* Drop down lists

### Binding to Text Fields

* input
    * Many textual input types, inlcuding HTML5 types are supported
* textarea

### Binding to Inputs

Two-Way Binding Example with an Input:

```JS

data: {
    appName: 'Growler',
    query: ''
}

```
NOTE:  You can not use the mustache syntax for model binding (v-model).
```HTML

<div id="growler">
    <input
    v-model="query"
    placeholder="search...">
    <div>Searching for: {{ query }}</div>
</div>

```

### Binding to Checkboxes

* Checkbox
* Checkbox List

Single Value:
```JS

data: {
    appName: 'Growler',
    isPowerSyntaxEnabled: false
}

```

```HTML

<input type="checkbox" v-model="isPowerSyntaxEnabled">

```

Multiple Values:

```JS

data: {
    appName: 'Growler',
    isPowerSyntaxEnabled: false,
    searchIndexes: []
}

```

```HTML
<label>
    <input
    type="checkbox" value="beers"
    v-model="searchIndexes">
    Beers
</label>
<br/>

<label>
    <input
    type="checkbox" value="breweries"
    v-model="searchIndexes">
    Breweries
</label>
<br/>

<small>
    selected: {{ searchIndexes }}
</small>

```

### Binding to Radio Buttons

Very similar to binding to multiple values (above).  Instead of an array, you bind to a single value from your model.  Toggling between the two radio buttons, toggles the value stored in the single value in the model.

```JS

data: {
    searchIndex: "beers"
}

```

```HTML

<input type="radio" value="beers" v-model="searchIndex">
<input type="radio" value="breweries" v-model="searchIndex">

```

#### Binding to Drop Downs

Nearly identical to binding to checkboxes and radio buttons.

### Modifying Bound Values



## Module 4:  Responding to User Events in Vue.js

## Module 5:  Conditional Rendering & Rendering of Lists

## Module 6:  Reacting to Data Changes with Filters, Computed Properties, & Watchers