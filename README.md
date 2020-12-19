# LearnReact-pro

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Intro to JSX
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

----------------
1.What is JSX?
----------------
JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does “syntax extension” mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can’t read it!

If a JavaScript file contains JSX code, then that file will have to be compiled. That means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.

------------------
2.JSX Elements
------------------
A basic unit of JSX is called a JSX element.

Here’s an example of a JSX element:

    <h1>Hello world</h1>

This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file.

--------------------------------------
3.JSX Elements And Their Surroundings
--------------------------------------

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go.

That means that a JSX element can be saved in a variable, passed to a function, stored in an object or array…you name it.

Here’s an example of a JSX element being saved in a variable:

=> const navBar = <nav>I am a nav bar</nav>;

Here’s an example of several JSX elements being stored in an object:

     const myTeam = {
      center: <li>Benzo Walli</li>,
      powerForward: <li>Rasha Loa</li>,
      smallForward: <li>Tayshaun Dasmoto</li>,
      shootingGuard: <li>Colmar Cumberbatch</li>,
      pointGuard: <li>Femi Billon</li>
    };

--------------------
4.Attributes In JSX
--------------------

JSX elements can have attributes, just like HTML elements can.

A JSX attribute is written using HTML-like syntax: a name, followed by an equals sign, followed by a value. The value should be wrapped in quotes, like this,

    my-attribute-name="my-attribute-value"

Here are some JSX elements with attributes:

    <a href='http://www.example.com'>Welcome to the Web</a>;
 
const title = <h1 id='title'>Introduction to React.js: Part I</h1>; 

A single JSX element can have many attributes, just like in HTML:

    const panda = <img src='images/panda.jpg' alt='panda' width='500px' height='500px' />;

----------------
5.Nested JSX
----------------

You can nest JSX elements inside of other JSX elements, just like in HTML.

Here’s an example of a JSX <h1> element, nested inside of a JSX <a> element:
  
    <a href="https://www.example.com"><h1>Click me!</h1></a>
 
To make this more readable, you can use HTML-style line breaks and indentation:

    <a href="https://www.example.com">
      <h1>
        Click me!
      </h1>
    </a>
    
If a JSX expression takes up more than one line, then you must wrap the multi-line JSX expression in parentheses. This looks strange at first, but you get used to it:

      (
        <a href="https://www.example.com">
          <h1>
            Click me!
          </h1>
        </a>
      )
  
Nested JSX expressions can be saved as variables, passed to functions, etc., just like non-nested JSX expressions can! Here’s an example of a nested JSX expression being saved as a variable: 

    const theExample = (
     <a href="https://www.example.com">
       <h1>
         Click me!
       </h1>
     </a>
    );
   
------------------------
 6.JSX Outer Elements
------------------------

There’s a rule that we haven’t mentioned: a JSX expression must have exactly one outermost element.

In other words, this code will work:

    const paragraphs = (
      <div id="i-am-the-outermost-element">
        <p>I am a paragraph.</p>
        <p>I, too, am a paragraph.</p>
      </div>
    );
But this code will not work:

     const paragraphs = (
      <p>I am a paragraph.</p> 
      <p>I, too, am a paragraph.</p>
    );
    
The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!

It’s easy to forget about this rule, and end up with errors that are tough to diagnose.

If you notice that a JSX expression has multiple outer elements, the solution is usually simple: wrap the JSX expression in a <div></div>.


----------------
7.Rendering JSX
---------------

You’ve learned how to write JSX elements! Now it’s time to learn how to render them.

To render a JSX expression means to make it appear onscreen.

The following code will render a JSX expression:
    
    import React from 'react';
    import ReactDOM from 'react-dom';
    ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));

JavaScript is case-sensitive, so make sure to capitalize ReactDOM correctly!

----------------------
8.ReactDOM.render() I
----------------------

Let’s examine the code that you just wrote. 

You can see something called ReactDOM. What’s that?
ReactDOM is the name of a JavaScript library. This library contains several React-specific methods, all of which deal with the DOM in some way or another.

Move slightly to the right, and you can see one of ReactDOM‘s methods: ReactDOM.render().

ReactDOM.render() is the most common way to render JSX. It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM. That is the way to make a JSX expression appear onscreen.

Move to the right a little more, and you come to this expression: 

        <h1>Hello world</h1>
        
This is the first argument being passed to ReactDOM.render(). ReactDOM.render()‘s first argument should be a JSX expression, and it will be rendered to the screen. 

------------------------
9.ReactDOM.render() II
------------------------

Move to the right a little more, and you will see this expression:

    document.getElementById('app')          
    
You just learned that ReactDOM.render() makes its first argument appear onscreen. But where on the screen should that first argument appear?

The first argument is appended to whatever element is selected by the second argument.
        
That element <main></main> acted as a container for ReactDOM.render()‘s first argument! At the end of the previous exercise, this appeared on the screen:

    <main id="app">
      <h1>Render me!</h1>
    </main>        
    
-------------------------------------------
10.Passing a Variable to ReactDOM.render()
-------------------------------------------

ReactDOM.render()‘s first argument should evaluate to a JSX expression, it doesn’t have to literally be a JSX expression.

The first argument could also be a variable, so long as that variable evaluates to a JSX expression.

In this example, we save a JSX expression as a variable named toDoList. We then pass toDoList as the first argument to ReactDOM.render():
        
    const toDoList = (
      <ol>
        <li>Learn React</li>
        <li>Become a Developer</li>
      </ol>
    );

    ReactDOM.render(
      toDoList, 
      document.getElementById('app')
    );        
    
--------------------
11.The Virtual DOM    
--------------------

One special thing about ReactDOM.render() is that it only updates DOM elements that have changed.

That means that if you render the exact same thing twice in a row, the second render will do nothing:

    const hello = <h1>Hello world</h1>;

    // This will add "Hello world" to the screen:

    ReactDOM.render(hello, document.getElementById('app'));

    // This won't do anything at all:

    ReactDOM.render(hello, document.getElementById('app'));

This is significant! Only updating the necessary DOM elements is a large part of what makes React so successful.

-----------
JSX Recap
-----------

Congratulations! You’ve learned to create and render JSX elements! This is the first step towards becoming fluent in React.

In the next lesson, you’ll learn some powerful things that you can do with JSX, as well as some common JSX issues and how to avoid them.
 
 
----------------------------------------------------------------------------------------------------------------------------------------------------------------- 
Advanced JSX        
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

-------------------
1.class vs className
--------------------

Grammar in JSX is mostly the same as in HTML, but there are subtle differences to watch out for. Probably the most frequent of these involves the word class.

In HTML, it’s common to use class as an attribute name:

    <h1 class="big">Hey</h1>
    
In JSX, you can’t use the word class! You have to use className instead:

    <h1 className="big">Hey</h1>
    
This is because JSX gets translated into JavaScript, and class is a reserved word in JavaScript.

When JSX is rendered, JSX className attributes are automatically rendered as class attributes.    

--------------------
2.Self-Closing Tags
--------------------

Another JSX ‘gotcha’ involves self-closing tags.

What’s a self-closing tag?

Most HTML elements use two tags: an opening tag (<div>), and a closing tag (</div>). However, some HTML elements such as <img> and <input> use only one tag. The tag that belongs to a single-tag element isn’t an opening tag nor a closing tag; it’s a self-closing tag.

When you write a self-closing tag in HTML, it is optional to include a forward-slash immediately before the final angle-bracket:

    Fine in HTML with a slash:

      <br />

    Also fine, without the slash:

      <br>

But!

In JSX, you have to include the slash. If you write a self-closing tag in JSX and forget the slash, you will raise an error:

    Fine in JSX:

      <br />

    NOT FINE AT ALL in JSX:

      <br>

------------------------------------------
3.JavaScript In Your JSX In Your JavaScript
-------------------------------------------

So far, we’ve focused on writing JSX expressions. It’s similar to writing bits of HTML, but inside of a JavaScript file.

In this lesson, we’re going to add something new: regular JavaScript, written inside of a JSX expression, written inside of a JavaScript file.

    ReactDOM.render(
      <h1>2 + 3</h1>,
      document.getElementById('app')
    );

---------------------
4.Curly Braces in JSX
---------------------
The code in the last exercise didn’t behave as one might expect. Instead of adding 2 and 3, it printed out “2 + 3” as a string of text. Why?

This happened because 2 + 3 is located in between 

    <h1> and </h1> tags.

Any code in between the tags of a JSX element will be read as JSX, not as regular JavaScript! JSX doesn’t add numbers - it reads them as text, just like HTML.

You need a way to write code that says, “Even though I am located in between JSX tags, treat me like ordinary JavaScript and not like JSX.”

You can do this by wrapping your code in curly braces.

    <h1>{2 + 3}</h1> //output - 5

---------------------------
5.(20) Digits of Pi in JSX
---------------------------

    import React from 'react';
    import ReactDOM from 'react-dom';

    const pi = (
      <div>
        <h1>
          PI, YALL!
        </h1>
        <p>
          {Math.PI.toFixed(20)}
        </p>
      </div>
    );

    ReactDOM.render(
        pi,
        document.getElementById('app')
    );
    
Study the expression and notice the following:

-> The code is written in a JavaScript file. By default, it will all be treated as regular JavaScript.

-> Find <div> on line 5. From there up through </div>, the code will be treated as JSX.

-> Find Math.From there up through (20), the code will be treated as regular JavaScript again.

-> The curly braces themselves won’t be treated as JSX nor as JavaScript. They are markers that signal the beginning and end of a JavaScript injection into JSX, similar to the quotation marks that signal the boundaries of a string.






        
        
        
        















