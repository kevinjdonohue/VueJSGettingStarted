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
* 

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

## Module 3:  Binding with Forms in Vue.js

## Module 4:  Responding to User Events in Vue.js

## Module 5:  Conditional Rendering & Rendering of Lists

## Module 6:  Reacting to Data Changes with Filters, Computed Properties, & Watchers