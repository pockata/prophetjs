# prophetjs
[![NPM](https://nodei.co/npm/prophetjs.png?downloads=true&stars=true)](https://nodei.co/npm/prophetjs/)
[![NPM](https://nodei.co/npm-dl/prophetjs.png?months=1&height=2)](https://nodei.co/npm/prophetjs/)

A very lean dependency free javascript library to display toast messages on web pages.
This project adheres to [Semantic Versioning](http://semver.org/). Sometimes I do screw up though. Prophet currently supports:
 - Chrome v26+
 - Firefox v20+
 - IE v10+ (sorry)
 - Safari v5+

#### Version 1.0.0

![default](https://github.com/binarybaba/prophetjs/raw/master/img/message-click-cb.gif)


#### Table of Contents
 - [Installation](#installation)
   - [Download](#get-the-files)
   - [Install](#find-the-files)
 - [Usage](#api)
   - [Simplest Display](#simplest-display)
   - [Callback](#callback)
   - [Options](#options)
   - [Custom Toast Types](#custom-types)
 - [Contributing](#contributing)
 - [License](#license)


## Installation

### Get the files:
Choose any of the ways to get prophet:

- clone from github `git clone https://github.com/binarybaba/prophetjs.git`
- Install from [npm](https://www.npmjs.com/package/prophetjs) `npm install prophetjs --save`
- Install from [bower](https://bower.io/search/?q=prophetjs) `bower install prophetjs --save`

### Find the files
You'll see the files in the dist folder:
  ```
  dist
  ├── css
  │   ├── prophet.css
  │   └── prophet.min.css
  └── js
      ├── prophet.js
      ├── prophet.js.map
      └── prophet-min.js
 ```
### Wire it up
 Include the css and js files in your webpage:

 `<link rel="stylesheet" href="dist/css/prophet.min.css">`

 `<script src="dist/js/prophet-min.js"></script>`
 
 `<ul class="prophet"></ul>`


# API

Prophet exposes a Message API. All customizations and configurations are done through this API.
To show a message, you will have to instantiate an instance of `Message`.

The toast message stays for a default duration of 4000 milliseconds or until the user clicks on it. After which,
the toast message is removed from the DOM.

#### Simplest display

`var toast = new Message('Harambe for president!').show();`

#### Callback

You can also provide a callback to every toast message. The callback will be triggered after the toast message is removed or
when the user clicks on it. The callback sends the autogenerated ID of the toast message (which can be overridden).

![callback](https://github.com/binarybaba/prophetjs/raw/master/img/message-click-cb.gif)
![no-callback](https://github.com/binarybaba/prophetjs/raw/master/img/message-default-no-click.gif)

```
var toast = new Message("Awesome! We'll contact you soon!", function(id){
    console.log('Message ID:', id);
    // some more code...
    });
    toast.show();
}
```

#### Options

You can also optionally include a set of options as a second argument (followed by the callback if any ) on every toast message. If the values are not implemented, the default values take up.
(Prophet was written in TypeScript which enforces type checking for development. Hence, it implements an interface IMessageOptions. More on that here...)
The following are the keys that options takes

 - `id`
	*The id is autogenerated per toast message.*
	 - default: auto-generated
	 - Type: number
 - `type`
 	*Prophet has 3 presets types:* `success`, `error` *and* `default`. *You can also set more presets. Click [here](#custom-types) to see how.*

 	![error](https://github.com/binarybaba/prophetjs/raw/master/img/message-error.gif)
 	 - default: `"default"`
 	 - Type: string
 - `duration`
	*The time each toast message stays on the web page before disappearing. Takes value in miliseconds.*
	 - default: `4000`
	 - Type: number

 - `class`
 	*You can further customize the look of every toast message by providing extra CSS classes to override. Takes a single string of class names seperated by spaces.*
 	 - default: `""`
 	 - Type: string

 ##### Example
 ```
 var ppap = new Message("Awesome! Pen Pineapple Apple Pen.", {
         id:i++, //i defined somewhere up above
         duration: 8000,
         type: 'success',
         class : 'blue-background white-text thin-border'
     }).show();
 ```

## Custom Types
You can also add more types by providing the `background-color`, `color` and `type` for more uses. Please note, all the keys are mandatory.

```
Message.config.types({
    type: "tip",
    backgroundColor:"#fafafa",
    color:"#313131"
})
```

Now you can use the type while invoking a new Message:

```
var ppap = new Message("Awesome! Pen Pineapple Apple Pen.", { type: 'tip'}, function(id){
     console.log(id);
 })
 ppap.show();
```
![stackUp](https://github.com/binarybaba/prophetjs/raw/master/img/message-stack-up.gif)


### Contributing
Thanks for taking out time for actually reading this block. You're awesome!
Prophetjs is written in [TypeScript](http://www.typescriptlang.org). I started writing this library as my venture into getting to know TypeScript better so if you're thinking of
contributing, please do install TypeScript as your dev dependencies. I'll be further updating this section to include guides on how to get
your way around the compiler and how you can install it per your IDE/editor (and maybe put this whole section in a new file)


#### License
Open source under the [MIT License](https://github.com/binarybaba/prophetjs/blob/master/LICENSE).
All rights reserved.
