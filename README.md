## What is this?

This document was created to serve as a universal JavaScript style guide to aid in collaboration as well as to keep my own code internally consistent.

The purpose of this guide is to provide a set of standards for the writing and design of Javascript code. Implementation of this guide will provide uniformity in code style and formatting in order to improve the quality of the code we are writing, making it consistent, readable, and maintainable. Ultimately code should appear as if it were written by one person. It should be easy for any third party to understand, use, and contribute to your code. Violations to this guide are allowed if they enhance readability.

Inspiration for this guide was taken from similar style guides such as those by [idiomatic](https://github.com/rwaldron/idiomatic.js), [airbnb](https://github.com/airbnb/javascript), [jQuery](http://contribute.jquery.org/style-guide/js/), [Google](https://google.github.io/styleguide/javascriptguide.xml), [Aloha](http://www.alohaeditor.org/guides/style_guide.html), [Dojo](https://dojotoolkit.org/reference-guide/1.9/developer/styleguide.html) and [other](https://www.google.com/) [sources](http://stackoverflow.com/) [around](https://github.com/) [the](http://www.mirc.com/) [web](https://developer.mozilla.org/en-US/). This document, like anything I make, is mostly an amalgamation of other people's wonderful ideas wrapped up in one place for my purposes. Efforts have been made to find a balance between clear/readable and compact/efficient. Of course, in the end this is my personally preferred set of coding conventions, and you're free to write your programs as you see fit within your own projects. If you see any problems with it, or think you could help to improve it, feel free to modify this document and submit a [pull request](https://help.github.com/articles/using-pull-requests/).

A certain amount of familiarity with the JavaScript language and programming in general will be assumed throughout.

## لا شيء يدوم

This is a living document. Expect it to be modified at any time to meet the current standards in practice in projects it may be applicable to.

## Table of Contents

  1. [Foreword](#what-is-this)
  1. [Conventions](#conventions)
    - [Linting](#1.4)
  1. [Choices](#choices)
    - [Indentation](#2.1)
    - [Quotation](#2.2)
  1. [Naming](#naming)
  1. [Declarations](#declarations)
    - [Literals](#4.1)
    - [Variables](#4.2)
  1. [Formatting](#formatting)
    - [Commas](#5.5)
    - [Whitespace](#5.7)
    - [Loops](#5.12)
  1. [Comments](#comments)
  1. [Further](#crabs)
  1. [HTML/CSS](#html)
    - (CSS)(#css)
  1. [Afterword](#ps)

## Conventions

  - [1.1](#1.1) <a name='1.1'></a> This is a style guide for JavaScript. Despite the availability of [compile to js languages](https://github.com/jashkenas/coffeescript/wiki/List-of-languages-that-compile-to-JS), all efforts should be made to keep our codebase purely in JavaScript.
  
  - [1.2](#1.2) <a name='1.2'></a> In keeping with this, we should also minimize our use of external libraries. This is for the sake of simplicity in reasoning about the code, as well as forcing us to actually know what we're doing and reducing the number of bugs caused by third-party code. The majority of our code should be written by us.
  
  - [1.3](#1.3) <a name='1.3'></a> Write with the intent of producing readable code. Expect that someone else will have to read and understand your code at some point. Use the correct [whitespace](#whitespace) and formatting to ensure readabililty. Finished code will be [minified](https://en.wikipedia.org/wiki/Minification_(programming)), so just write nicely.

  - [1.4](#1.4) <a name='1.4'></a> If it wasn't already obvious from the webpage you're likely viewing this from, our projects will be managed through [github](https://github.com/). If you aren't familiar with github, [here's a quick primer](http://rogerdudler.github.io/git-guide/). You should have a basic understanding of git, it's simple and useful. 

  - [1.5](#1.5) <a name='1.5'></a> Use [JSHint](http://jshint.com/) for linting. Linting helps to detect and fix errors, and is considered good practice.
  
## Choices
  
Much like the [oxford comma](https://en.wikipedia.org/wiki/Serial_comma), there are many things within JavaScript that are simply a matter of [preference](http://sideeffect.kr/popularconvention/#javascript). I've made these choices in regards to my own preferences when working with JavaScript. These are things that are entirely at the discretion of the project authors. JavaScript handles them exactly the same way internally. The only thing that is important, is consistency. Pick one and stick to it for the entire project. For your consideration:
  
  - [2.1](#2.1) <a name='2.1'></a> Indentation choice. Whether you use real tabs or soft indents(spaces), and, if you should choose soft tabs, whether you indent by 2 or 4 spaces. [Crockford](http://javascript.crockford.com/code.html#indentation) and [others](https://github.com/pegurnee) argue against the use of tabs for indentation, as there is no standard way of handling tabstops. Indenting by spaces can increase filesize in a large project, but this is mitigated in the minification process, and should not be a concern. Never mix tabs and spaces.
  
  Opt for the use of soft tabs for indentation.
  
  - [2.2](#2.2) <a name='2.2'></a> Whether you use single or double quotations. If double quotations are used, single quotes are allowed for inner quotes, and vice versa for single quotes.
  
  Single quote style is preferred, with double quotes within strings. The [majority](http://sideeffect.kr/popularconvention/#javascript) of javascript code on github uses this style.

## Naming
  - [3.1](#3.1) <a name='3.1'></a> Names should be written in short, simple, descriptive English.
  
  - [3.2](#3.2) <a name='3.2'></a> Use CamelCase for class names and mixedCase for method and property names.

  - [3.3](#3.3) <a name='3.3'></a> Names should be easy to understand. Favor naming to functionality over values.
  
  - [3.4](#3.4) <a name='3.4'></a> Avoid names that are misleading, or have multiple meanings.
  
  - [3.5](#3.5) <a name='3.5'></a> Don't obfuscate names, for example by removing all vowels. Understandable abbreviations are acceptable, but in general should be avoided. The main point is to keep it humanly readable.
  ```javascript
  // BAD
  var objPosX = 0;
  
  // GOOD
  var objectPositionX = 0;
  ```
  
  - [3.6](#3.6) <a name='3.6'></a> Avoid magic numbers, use named constants. Program for the future. Constants should be named in all caps, with underscores used to separate words.
  ```javascript
  var SOME_CONSTANT = 123.45;
  ```
  
  - [3.7](#3.7) <a name='3.7'></a> Don't use the underscore character, except as noted in [3.6](#3.6) and [3.9](#3.9).
  ```javascript
  // BAD
  unitPos_X
  
  // GOOD
  unitPositionX
  ```
  
  - [3.8](#3.8) <a name='3.8'></a> Method names should be verbs.
  
  - [3.9](#3.9) <a name='3.9'></a> Methods and properties that are determined to be private should be prepended with an underscore (_)

  - [3.10](#3.10) <a name='3.10'></a> Use is or has/can/should for boolean variables and methods. Avoid negated booleans.
  ```javascript
  // BAD
  var isNotThing = true;
  
  // GOOD
  var isThing = false;
  ```
  
  - [3.11](#3.11) <a name='3.11'></a> Use compute when naming functions that perform computations.
  
  - [3.12](#3.12) <a name='3.12'></a> Use find when naming functions that looks up some value.
  
  - [3.13](#3.13) <a name='3.13'></a> Methods may be named after what they return. If the return void instead of an object then after what they do.
  
  - [3.14](#3.14) <a name='3.14'></a> Collections should be plural.
  ```javascript
  // BAD
  var animalList = [];
  
  // GOOD
  var animals = [];
  ```
  
  - [3.15](#3.15) <a name='3.15'></a> Iterators should be named i, j, k, etc. They should be defined in the loop constructor. This is significantly more readable than anticipating variable hoisting.
  
  - [3.16](#3.16) <a name='3.16'></a> Avoid checking for array length in every iteration of a loop. Set another variable to hold the length in the loop constructor.
  ```javascript
  var l = someArray.length;
  for(var i = 0; i < l; i++) {
  	doSomethingTo(someArray[i]);
  }
  ```

  - [3.17](#3.17) <a name='3.17'></a> Generic variables should have the same name as their type.
  ```javascript
  //where topic is of type Topic
  setTopic(topic)
  ```

  - [3.18](#3.18) <a name='3.18'></a> Initialization methods should be named init().
  ```javascript
  // BAD
  initialize()
  initializeSomething()
  start()
  run()
  
  // GOOD
  init()
  initSidebar()
  ```

  - [3.19](#3.19) <a name='3.19'></a> Don’t use “that” to refer to an outer “this”. Use the name of the class instead (with first char lowercased).
  ```javascript
  var MyObject = Class.extend({
    _constructor: function() {
      // BAD
      var that = this;
      setTimeout(function() {
        console.log(that.name + ' done.');
      };
          
      // GOOD
      var myObject = this;
      setTimeout(function() {
        console.log(myObject.name + ' done.');
      };
    }
  });
  ```

## Declarations

  - [4.1](#4.1) <a name='4.1'></a> Use literal syntax for objects and arrays
  ```javascript
  // BAD
  var squid = new Object();
  var reefs = new Array();
  
  // GOOD
  var squid = {};
  var reefs = [];
  ```

  - [4.2](#4.2) <a name='4.2'></a> Initialize variables where they're declared, even if it's a null declaration.
  ```javascript
  // BAD
  var someObj, someArr;
  
  // GOOD
  var someObject = {};
  var someArray = [];
  ```

## Formatting

  - [5.1](#5.1) <a name='5.1'></a> ALWAYS use brackets and semicolons where applicable. Never rely on automatic insertion.
  
  - [5.2](#5.2) <a name='5.2'></a> Related variables of the same type should be declared in a common statement. Unrelated variables or those of different type must have a separate var declaration.
  ```javascript
  // BAD
  var someObj, anArray, counter, height;
  
  // GOOD
  var someObject = {};
  var anArray = [];
  var counter, height;
  ```
  
  - [5.3](#5.3) <a name='5.3'></a> Floating point constants should always be named with at least one number before and after the decimal point.
  ```javascript
  var position.x = 0.0;
  ```
  
  - [5.4](#5.4) <a name='5.4'></a> An effort should be made to contain scope for the purpose of keeping variables alive for the smallest amount of time possible.
  
  - [5.5](#5.5) <a name='5.5'></a> Commas should be followed by a space or newline.
  ```javascript
  // BAD
  shape = new THREE.BoxGeometry(width,height,depth);
  
  // GOOD
  shape = new THREE.BoxGeometry(width, height, depth);
  ```
  
  - [5.6](#5.6) <a name='5.6'></a> No preceding space on commas or semicolons.
  ```javascript
  // BAD
  someObject.functionCall( arg1 , arg2 , arg3 );
  
  // GOOD
  someObject.functionCall(arg1, arg2, arg3);
  ```
  
  - [5.7](#5.7) <a name='5.7'></a> No whitespace at eol or on blank lines.
  ```javascript
  //this is important
  ```
  
  - [5.8](#5.8) <a name='5.8'></a> Assignment operators should have a space on either side.
  ```javascript
  // BAD
  frame=i;
  
  // GOOD
  frame = i;
  ```
  
  - [5.9](#5.9) <a name='5.9'></a> Unary operators(!, ++) should not have a space next to their operator.
  ```javascript
  // BAD
  balls = - Math.RandInt(10,160);
  ballCount ++;
  
  // GOOD
  balls = -Math.RandInt(10, 160);
  ballCount++;
  ```
  
  - [5.10](#5.10) <a name='5.10'></a> Semicolons used as statement terminators should be followed by a newline.
  
  - [5.11](#5.11) <a name='5.11'></a> Avoid filler spaces, especially in empty constructs such as {}, [], and function().
  
  - [5.12](#5.12) <a name='5.12'></a> If statements, for loops, while loops, and function declarations should have their opening brace on the same line, separated by a space.
  ```javascript
  // BAD
  if(condition){functionCall();}
  
  if(condition)
  {
    functionCall();
  }
  
  // GOOD
  if(condition) {
    functionCall();
  }
  ```

  - [5.13](#5.13) <a name='5.13'></a> [Ternary conditionals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) should have a space on either side of their operators.
  ```javascript
  condition ? expression1 : expression2;
  ```

  - [5.14](#5.14) <a name='5.14'></a> Logical units within a block should be separated by one blank line. Do not use multiple consecutive blank lines in your programs.
  
  - [5.15](#5.15) <a name='5.15'></a> There is no hard limit on line length but be reasonable. If you need a number then 80 or 120 characters, including whitespace, are common restrictions.

  - [5.16](#5.16) <a name='5.16'></a> Split line positioning for expressions and methods:
  ```javascript
  var someExpression = Expression1
    + Expression2
    + Expression3
  ;
  
  var o = someObject.get(
    Expression1,
    Expression2,
    Expression3
  );
  ```

## Comments

  - [6.1](#6.1) <a name='6.1'></a> It is often said that good code is its own documentation. This is a wonderful ideal but, since we are not the golden gods of clear and readable code, we'll use comments where applicable.
  
  - [6.2](#6.2) <a name='6.2'></a> Comments should be concise and descriptive. Only write what you need, no more. We aren't going to run out of ink, but if you comment every single line you're an asshole. Prefer writing for readability over commenting on functionality.
  
  - [6.3](#6.3) <a name='6.3'></a> All comments should be written in [American English](https://www.youtube.com/watch?v=CAV0XrbEwNc) for the sake of uniformity.
  
  - [6.4](#6.4) <a name='6.4'></a> Comments should be indented relative to their position in the code, above the code the describe. Single line comments to the right of the code are also acceptable.
  
  - [6.5](#6.5) <a name='6.5'></a> Collections should be commented describing the common elements.
  
  - [6.6](#6.6) <a name='6.6'></a> Large blocks should be commented.
  
  - [6.7](#6.7) <a name='6.7'></a> Inline comments should be avoided.
  
  - [6.8](#6.8) <a name='6.8'></a> Comments found to be in violation of [t](#6.1)[h](#6.2)[e](#6.3)[s](#6.4)[e](#6.8) rules will be pruned with extreme prejudice.

## Additional Considerations <a name='crabs'></a>

  - [7.1](#7.1) <a name='7.1'></a> When building strings programmatically, use [template strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/template_strings).
  ```javascript
  //bad
  function sayHi(name) {
    return 'How are you, ' + name + '?';
  }
 
  //good
  function sayHi(name) {
    return `How are you, ${name}?`;
  }
  ```
  
  - [7.2](#7.2) <a name='7.2'></a> Always use strict equality checks (===). The only situation where you would use a loose inequality operator (==) is if you are checking for something that could be null or undefined by way of == null, such as in the case of uninitialized variables.

  - [7.3](#7.3) <a name='7.3'></a> You can emulate enums in the style of C by using a single object as a holder for all your constants, naturally written in all caps.
  ```javascript
  var someEnum {
    ONE_THING: 0,
    ANOTHER_THING: 1,
    THIRD_THING: 2
  }
  ```
  
  - [7.4](#7.4) <a name='7.4'></a> Singletons are useful for objects that have state.
  ```javascript
  var pezDispenser = (function() {
    var amount = 20;
    return {
      dispense: function() {
        if (amount > 0) }
          amount -= 1;
          alert('delicious pez!');
        } else {
          alert('no more pez!');
        }
      }
    };
  }());

  pezDispenser.dispense();
  ```
  Simply name the function and refrain from invoking it immediately and you have what amounts to a constructor.
  
  - [7.5](#7.5) <a name='7.5'></a> [Don't use eval()](http://stackoverflow.com/questions/86513/why-is-using-the-javascript-eval-function-a-bad-idea), okay?

  - [7.6](#7.6) <a name='7.6'></a> Don't worry about using the [new](http://stackoverflow.com/a/383503/5831292) keyword. I mean, use it, obviously, just don't be concerned that you're doing something 'bad'.
  
  - [7.7](#7.7) <a name='7.7'></a> If you're going to use the delete operator, make sure you [understand how it works](http://perfectionkills.com/understanding-delete/). In general it is used to remove object properties. NOT for variables, function arguments, or function identifiers. If you need to free up a reference for GC then setting it to null would be the preferred notation. Setting an object to null will also clean up all of the properties of that object.

  - [7.8](#7.8) <a name='7.8'></a> Don't pass strings to setInterval() or setTimeout(). Passing in strings is both painfully slow and potentially insecure. If you pass in a string, javascript will hand it to the function constructor to be converted into a new function. Instead pass in a function reference or an anonymous function.

## HTML/CSS <a name='html'></a>

  - HTML formatting should be compact yet readable. Formal definitions of HTML style yet to be decided. Reference existing files and make good decisions.

  - ### [CSS](#CSS)
  CSS files follow basically the same set of conventions as javascript.
    - Each selector is on a new line
    - Opening curly braces are preceded by a space
    - Key value pairs have a space after the colon
    - Every block is followed by an empty new line
  ```
  .className {
    color: #800080;
  }

  .className,
  #anId {
    color: #00CA00;
  }
  ```

## 後付 <a name='ps'></a>

Thanks for reading! Feel free to [contact me](mailto:jkarbows@gmail.com) if there's anything you'd like to say.

---------------


<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
