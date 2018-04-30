# JS Cheatsheet

## Selecting by ID
    document.getElementById('someId');

    // example
    const myHeading = document.getElementById('myHeading');

## Selecting Elements by Tag
    document.getElementsByTagName('some_tag');

## Selecting using Querying (Searching with CSS)
    // Returns All elements found
    document.querySelectorAll('#some_id')
    document.querySelectorAll('#rainbow > li')
    document.querySelectorAll('.some_class')
    document.querySelectorAll('li')

    // Returns First Element Found
    document.querySelector('li')


## Adding Listeners
    document_obj.addEventListener('<typeOfEvent>', <function>);

    // example
    myHeading.addEventListener('click', () => {
        myHeading.style.color = 'red';
    });

### [Event Types](https://developer.mozilla.org/en-US/docs/Web/Events)
* `load`
* `click`
* `dbclick`
* `mousedown`
* `mouseup`
* `mousemove`
* `mouseover`
* `mouseout`
* `keydown`
* `keyup`
* `keypress`

### Tablet and Smartphone Types
* `touchstart`
* `touchmove`
* `touchend`



## Check if an Html element contains a class
    <element>.classList.contains('some_class');

## Getting and setting Text of Elements
    element.textContent 

    // Setting text 
    element.textContext = "Some text";

## Getting and Setting innerHtml of elements
    element.innerHtml

    //setting
    element.innerHtml = "<p>I'm changing this element's innerHtml</p>"

## Getting and setting Type of elements
    element.type
    element.type = 'checkbox'

## Creating Elements
    // This does not insert an element into the page
    let li = document.createElement('li');
    li.textContent = "something";

## Appending Elements inside of other elements.
    <Parent_element>.appendChild(<child_element>)

## Deleting Elements inside of other elements.
    <Parent_element>.removeChild(<child_element>)

## Anonymous Function
Often used when writing simple functions to be passed as an argument to another function.

    (something) => { console.log(something) }

## [Window.setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/WindowTimers/setTimeout)
Window object has a setTimeout function we can use to delay the execution of a function

    window.setTimeout((something) => { console.log(something);
    }, 3000, 'Greetings. everyone!');

## Bubbling w/ Event Handlers
    document.addEventListener('click', (event) => {
        console.log(event.target)
    });

    <--! List Elements Example (When moused over li text are uppercased) -->
    const listDiv = document.getElement...........

    listDiv.addEventListener('mouseover', (event) => {
        if (event.target.tagName == 'LI') {
            event.target.textContent = event.target.textContent.toUpperCase();
        }
    });

## Getting Parent Elements from their Children
    <childElement>.parentNode

## Getting Previous Siblings
    <sibling_element>.previousElementSibling

## Inserting an element before a given element
    <parent_element>.insertBefore(<new_node>, <reference_node>)

## Getting all children of a parent node
    <parent_element>.children

    <!-- you can index the children -->
    <parent_element>.children[1]

## Getting first and last elements of Parent's child elements
    <parent_node>.firstElementChild
    <parent_node>.lastElementChild

## Getting Next Sibling Element
    <selected_element>.nextElementSibling

***

## Iterators

### forEach
Will return undefined

    let fruits = ['Mango', 'Papaya', 'Pineapple', 'Apple'];

    fruits.forEach(function(fruit) {console.log('I want to eat a ' + fruit);})

    or (using anonymous function)

    fruits.forEach(fruit => console.log(`I want to eat ${fruit}))

### map 
    let bigNumbers = [100, 200, 300, 400, 500];

    let smallNumbers = bigNumbers.map(num => num / 1000)

### filter
    let words = ['chair', 'music', 'pillow', 'brick', 'pen', 'door'];

    let shortWords = words.filter(word => word.length < 6);

### some
Returns true if the condition is met by any of the elements within a list.

    let words = ['unique', 'uncanny', 'pipque', 'oxymoron', 'guise'];

    console.log(words.some(word => word.length < 6))

### every
Returns true if the condition is met by all elements within a list.

    let words = ['unique', 'uncanny', 'pipque', 'oxymoron', 'guise'];

    console.log(words.every(word => word.length < 6))    

***
## Objects

*FYI: Objects w/in objects seem to prefer single quoted strings*

### Objects with Methods

    let myObject = {
        name: "George",
        myMethod: () => return "hi",
        myOtherMethod() {
            return "good evening";
        },
        anotherMethod: function() {
            return "Ohhhhhhh";
        }
        myNameIs() {
            return "my name is ${this.name}";
        }
    }

### this

    let myObject = {
        name: "George",
        myMethod: () => return "hi", // avoid using keyword 'this' with this syntax
        myNameIs() {
            return "my name is ${this.name}";
        }
    }

    let friend = {name: 'Jimmy'};

    friend.myNameIs = myObject.myNameIs

    console.log(friend.myNameIs()) // my name is jimmy

### setters

    let myObject = {
        _name: "George",
        set name(newName) {
            if (typeof newName === 'string'){
                this._name = newName;
            }
            else {
                console.log("${newName} is not valid");
            }
        }
    }

###### Using setter method

    myObject.name = "Ronny";

### getters

    let myObject = {
        _name: "George",
        set name(newName) {
            if (typeof newName === 'string'){
                this._name = newName;
            }
            else {
                console.log("${newName} is not valid");
            }
        },
        get name() {
            console.log(`My name is ${this._name}`)
        },
    }
***
## Classes

    class Dog {
        constructor(name) {
            this.name = name;
            this.behavior = 0;
        }
    }

### Creating an instance

    const jack = new Dog("Jack")

### getters

    class Dog {
        constructor(name) {
            this._name = name;
            this._behavior = 0;
        }

        get name() {
            return this._name;
        }
    }

### methods

    class Dog {
        constructor(name) {
            this._name = name;
            this._behavior = 0;
        }

        bark() {
            console.log("bark");
        }
    }

### Inheritence

    class Animal {
        constructor(name) {
            this._name = name;
            this._behavior = 0;
        }
    }

    class Cat extends Animal {
        constructor(name, usesLitter) {
            super(name);
            this._usesLitter = usesLitter;
        }
    }

### Static Methods

    class Animal {
        constructor(name) {
            this._name = name;
            this._behavior = 0;
        }

        static generatePassword() {
            return Math.floor(Math.random() * 10000);
        }
    }
***
## [Can I Use](https://caniuse.com/)
***
## Installing Node packages
The `npm` install command creates a folder called `node_modules` and copies the package files to it. The install command also installs all of the dependencies for the given package.
***
## Working with Babel

### Installation
    // babel-cli package includes command line Babel tools
    $ npm install babel-cli -D

    // babel-preset-env maps any JavaScript feature, ES6 and above (ES6+), to ES5
    $ npm install babel-preset-env -D

    // The -D flag instructs npm to add each package to a property called devDependencies in package.json. Other developers can now run your project without installing each package separately, they simply run npm install. This instructs npm to look inside package.json and download all of the packages listed in devDependencies.

### Setting up a JS project to use `npm`
Command creates a package.json file in the root directory

A package.json file contains information about the current JavaScript project. Some of this information includes:

* Metadata — This includes a project title, description, authors, and more.
* A list of node packages required for the project — If another developer wants to run your project, npm looks inside package.json and downloads the packages in this list.
* Key-value pairs for command line scripts — You can use npm to run these shorthand scripts to perform some process. In a later exercise, we will add a script that runs Babel and transpiles ES6 to ES5.

```bash
// run at project root
$ npm init

$ touch .babelrc
$ vim .babelrc

// add the following

{
    "presets": ["env"]
}

// inside package.json below "test" but inside "scripts".
"build": "babel src -d lib",

// Now you can run the following to transpile your code
$ npm run build
```
***

## Modules
You may combine methods of exporting (and importing) but typically it is best to avoid. A case is which you might combine is when you suspect devs may only be interested in importing a specific function and won't need to timport the entire export.

### Exporting

    let Menu = {};
    Menu.specialty = "Roasted Beet Burger with Mint Sauce";

    module.exports = Menu;

    // or

    let Menu = {};

    module.exports = {
        specialty: "Roasted Beet Burger with Mint Sauce",
        getSpecialty: function() {
            return this.specialty;
        }
    };

#### export default (ES6 Syntax)

    let Menu = {};

    export default Menu;

#### Named exports (ES6)

    let specialty = '';
    function isVegetarian(){
    };
    function isLowInSodium(){
    };

    export { specialty, isVegetarian };

    // or

    export let specialty = '';
    export function isVegetarian(){
    };
    function isLowInSodium(){
    };

#### Export as (ES6)

    let specialty = '';
    function isVegetarian(){
    };
    function isLowInSodium(){
    };

    export { specialty as chefsSpecial, isVegetarian as isVeg, isLowInSodium};

### Importing (require)

    const Menu = require('./menu.js');

    function placeOrder() {
        console.log('My order is: ' + Menu.specialty);
    }

    placeOrder()

#### import (ES6)

    import Menu from './menu';

#### Named imports (ES6)

    import { specialty, isVegetarian } from './menu';

    console.log(specialty)

#### Import as (ES6)
See export as too (above)

    import { chefsSpecial, isVeg } from './menu';

## AJAX

### GET request

    const xhr = new XMLHttpRequest();
    const url = "your_URL";
    xhr.responseType = 'json';
    xhr.onreadystatechange = function() {
        if (xhr.readyState === XMLHttpRequest.DONE) {
            console.log(xhr.response);
        }
    };
    xhr.open('GET', url)

### POST request

    const xhr = new XMLHttpRequest();
    const url = 'https://api-to-call.com/endpoint';
    const data = JSON.stringify({id: '200'});

    xhr.responseType = 'json';
    xhr.onreadystatechange = function() {
    if (xhr.readyState === XMLHttpRequest.DONE) {
        console.log(xhr.response);
    }
    }
    xhr.open('POST', url);
    xhr.send(data)

### jQuery 

#### AJAX GET

    $.ajax({
        url: 'https://api-to-call.com/endpoint',
        type: 'GET',
        dataType: 'json',
        success(response) {
            console.log(response)
        },
        error(jqXHR, status, errorThrown) {
            console.log(jqXHR)
        }
    });

#### AJAX POST

    $.ajax({
        url: 'https://api-to-call.com/endpoint',
        type: 'POST',
        data: JSON.stringify({id: 200}),
        dataType: 'json',
        success(response) {
            console.log(response);
        },
        error(jqXHR, status, errorThrown) {
            console.log(jqXHR);
        }
    });

#### $.get()

    $.get('https://api-to-call.com/endpoint', response => {...}, 'json');

####$.post()

    $.post({
        url: urlWithKey, 
        data: JSON.stringify({longUrl: urlToShorten}), 
        dataType: 'json', 
        contentType: 'application/json', 
        success(response) {
            console.log(response);
        },
        error(jqXHR, status, errorThrown) {
            console.log(jqXHR);
        }
    });

#### $.getJSON()

    $.getJSON(url, 
       response => {
           console.log(response)
    });

### fetch() GET REQUEST

    fetch('https://api-to-call.com/endpoint').then(response => {
      if (response.ok) {
        return response.json();
      } 
      throw new Error('Request failed!');
    }, networkError => console.log(networkError.message)
    ).then(jsonResponse => jsonResponse)

### fetch() POST REQUEST

    fetch('https://api-to-call.com/endpoint',
    {
        method: 'POST',
        body: JSON.stringify({id: '200'}),
    }
    ).then(
    response => {
        if (response.ok) {
            return response.json();
        }
        throw new Error('Request failed!');
        },
        networkError => console.log(networkError.message)
    ).then(
        jsonResponse => jsonResponse
    )

### async GET Requests (ES7)

    async function getData() {
        try {
            let response = await fetch('https://api-to-call.com/endpoint')
            if (response.ok) {
                let jsonResponse = await response.json();
                return jsonResponse;
            }
            throw new Error('Request failed!');
        }
        catch(error) {
            console.log(error);
        }
    }

### async POST Requests

    async function getData() {
        try {
            let response = await fetch(
                'https://api-to-call.com/endpoint', 
                {
                    method: 'POST',
                    body: JSON.stringify({id: 200})
                }
            );
            if (response.ok) {
                let jsonResponse = await response.json();
                return jsonResponse;
            }
            throw new Error('Request failed!');
        }
        catch (error) {
            console.log(error);
        }
    };