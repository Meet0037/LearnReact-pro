# LearnReact-pro

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
A.Intro to JSX
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

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
B.Advanced JSX        
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


-------------------
6.Variables in JSX
------------------

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.

    // Declare a variable:
    const name = 'Gerdo';

    // Access your variable 
    // from inside of a JSX expression:
    const greeting = <p>Hello, {name}!</p>;
    
------------------------------
7.Variable Attributes in JSX
------------------------------

When writing JSX, it’s common to use variables to set attributes.

Here’s an example of how that might work:

    // Use a variable to set the `height` and `width` attributes:

    const sideLength = "200px";

    const panda = (
      <img 
        src="images/panda.jpg" 
        alt="panda" 
        height={sideLength} 
        width={sideLength} />
    );        
    
Notice how in this example, the <img />‘s attributes each get their own line. This can make your code more readable if you have a lot of attributes on one element.

Object properties are also often used to set attributes:  

    const pics = {
      panda: "http://bit.ly/1Tqltv5",
      owl: "http://bit.ly/1XGtkM3",
      owlCat: "http://bit.ly/1Upbczi"
    }; 

    const panda = (
      <img 
        src={pics.panda} 
        alt="Lazy Panda" />
    );

    const owl = (
      <img 
        src={pics.owl} 
        alt="Unimpressed Owl" />
    );

    const owlCat = (
      <img 
        src={pics.owlCat} 
        alt="Ghastly Abomination" />
    ); 
        
-------------------------
8.Event Listeners in JSX
------------------------

JSX elements can have event listeners, just like HTML elements can. Programming in React means constantly working with event listeners.

You create an event listener by giving a JSX element a special attribute. Here’s an example:

    <img onClick={myFunc} />
    
An event listener attribute’s name should be something like onClick or onMouseOver: the word on, plus the type of event that you’re listening for.
An event listener attribute’s value should be a function. The above example would only work if myFunc were a valid function that had been defined elsewhere:

    function myFunc() {
      alert('Make myFunc the pFunc... omg that was horrible i am so sorry');
    }

    <img onClick={myFunc} />

Note : In HTML, event listener names are written in all lowercase, such as onclick or onmouseover. In JSX, event listener names are written in camelCase, such as onClick or onMouseOver.

------------------------------------------------
9.JSX Conditionals: If Statements That Don't Work
------------------------------------------------

Great work! You’ve learned how to use curly braces to inject JavaScript into a JSX expression! Here’s a rule that you need to know: you can not inject an if statement into a JSX expression.

This code will break:

    (
      <h1>
        {
          if (purchase.complete) {
            'Thank you for placing an order!'
          }
        }
      </h1>
    )

---------------------------------------------
10.JSX Conditionals: If Statements That Do Work
---------------------------------------------

How can you write a conditional, if you can’t inject an if statement into JSX?

    import React from 'react';
    import ReactDOM from 'react-dom';

    let message;

    if (user.age >= drinkingAge) {
      message = (
        <h1>
          Hey, check out this alcoholic beverage!
        </h1>
      );
    } else {
      message = (
        <h1>
          Hey, check out these earrings I got at Claire's!
        </h1>
      );
    }

    ReactDOM.render(
      message, 
      document.getElementById('app')
    );

Well, one option is to write an if statement, and not inject it into JSX.

Look at if.js. Follow the if statement, all the way from line 6 down to line 18.

if.js works, because the words if and else are not injected in between JSX tags. The if statement is on the outside, and no JavaScript injection is necessary.

This is a common way to express conditionals in JSX.

Note : !!! Remember: semi-colons are used in JavaScript, but not within JSX expressions!

       // like this
      img = (
        <img src={pics.kitty} />
      );
    // NOT like this
      img = (
        <img src={pics.kitty} />;
      )

-----------------------------------------
11.JSX Conditionals: The Ternary Operator
-----------------------------------------

There’s a more compact way to write conditionals in JSX: the ternary operator.

The ternary operator works the same way in React as it does in regular JavaScript. However, it shows up in React surprisingly often.

Recall how it works: you write x ? y : z, where x, y, and z are all JavaScript expressions. When your code is executed, x is evaluated as either “truthy” or “falsy.” If x is truthy, then the entire ternary operator returns y. If x is falsy, then the entire ternary operator returns z.

Here’s how you might use the ternary operator in a JSX expression:

    const headline = (
      <h1>
        { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
      </h1>
    );
    
In the above example, if age is greater than or equal to drinkingAge, then headline will equal Buy Drink. Otherwise, headline will equal Do Teen Stuff.

-------------------------------
12.JSX Conditionals: &&
--------------------------------

We’re going to cover one final way of writing conditionals in React: the && operator.

Like the ternary operator, && is not React-specific, but it shows up in React surprisingly often.

In the last two lessons, you wrote statements that would sometimes render a kitty and other times render a doggy. && would not have been the best choice for those lessons.

&& works best in conditionals that will sometimes do an action, but other times do nothing at all. 

Here’s an example:

    const tasty = (
      <ul>
        <li>Applesauce</li>
        { !baby && <li>Pizza</li> }
        { age > 15 && <li>Brussels Sprouts</li> }
        { age > 20 && <li>Oysters</li> }
        { age > 25 && <li>Grappa</li> }
      </ul>
    );
    
If the expression on the left of the && evaluates as true, then the JSX on the right of the && will be rendered. If the first expression is false, however, then the JSX to the right of the && will be ignored and not rendered.

----------------------
13..map in JSX
----------------------

The array method .map() comes up often in React. It’s good to get in the habit of using it alongside JSX.

If you want to create a list of JSX elements, then .map() is often your best bet. It can look odd at first:

    const strings = ['Home', 'Shop', 'About Me'];

    const listItems = strings.map(string => <li>{string}</li>);

    <ul>{listItems}</ul>
    
In the above example, we start out with an array of strings. We call .map() on this array of strings, and the .map() call returns a new array of <li>s.

On the last line of the example, note that {listItems} will evaluate to an array, because it’s the returned value of .map()! JSX <li>s don’t have to be in an array like this, but they can be.

// This is fine in JSX, not in an explicit array:
 
    <ul>
      <li>item 1</li>
      <li>item 2</li>
      <li>item 3</li>
    </ul>

    // This is also fine!

    const liArray = [
      <li>item 1</li>, 
      <li>item 2<li>, 
      <li>item 3</li>
    ];

    <ul>{liArray}</ul>    

Ex : 

    import React from 'react';
    import ReactDOM from 'react-dom';

    const people = ['Rowe', 'Prevost', 'Gare'];

    const peopleLis = people.map(person => <li>{person}</li>
      // expression goes here:

    );

    // ReactDOM.render goes here:
    ReactDOM.render(
      <ul>{peopleLis}</ul>,
      document.getElementById('app')
    );
    
    //Output:
    
                                                Rowe
                                                Prevost
                                                Gare
                                                
 ----------------------
 14.Keys
 ---------------------
 
 When you make a list in JSX, sometimes your list will need to include something called keys:

     <ul>
      <li key="li-01">Example1</li>
      <li key="li-02">Example2</li>
      <li key="li-03">Example3</li>
    </ul>
    
A key is a JSX attribute. The attribute’s name is key. The attribute’s value should be something unique, similar to an id attribute.

keys don’t do anything that you can see! React uses them internally to keep track of lists. If you don’t use keys when you’re supposed to, React might accidentally scramble your list-items into the wrong order.

Not all lists need to have keys. A list needs keys if either of the following are true:

1. The list-items have memory from one render to the next. For instance, when a to-do list renders, each item must “remember” whether it was checked off. The items shouldn’t get amnesia when they render.

2. A list’s order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don’t have to worry about keys. If you aren’t sure then it never hurts to use them!

------------------------
15.React.createElement
------------------------

You can write React code without using JSX at all!

The majority of React programmers do use JSX, and we will use it for the remainder of this tutorial, but you should understand that it is possible to write React code without it.

The following JSX expression:

    const h1 = <h1>Hello world</h1>;
    
can be rewritten without JSX, like this:

    const h1 = React.createElement(
      "h1",
      null,
      "Hello, world"
    );
    
When a JSX element is compiled, the compiler transforms the JSX element into the method that you see above: React.createElement(). Every JSX element is secretly a call to React.createElement().

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
B.Your First React Component
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

----------------------------------------
1.Hello World, Part II... THE COMPONENT
----------------------------------------

What’s a component?

A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML.

Take a look at the code below. This code will create and render a new React component: 

    import React from 'react';
    import ReactDOM from 'react-dom';

    class MyComponentClass extends React.Component {
      render() {
        return <h1>Hello world</h1>;
      }
    };

    ReactDOM.render(
      <MyComponentClass />,
      document.getElementById('app')
    );
    
A lot of that code is probably unfamiliar. However you can recognize some JSX in there, as well as ReactDOM.render().

-------------------------------------
2.Import React
--------------------------------------
Wooo! Your first React component!

Take a look at the code on line 1:

    import React from 'react';
    
This imported object contains methods that you need in order to use React. The object is called the React library.

Later, we’ll go over where the React library is imported from, and how the importing process works. For now, just know that you get the React library via import React from 'react';.

You’ve already seen one of the methods contained in the React library: React.createElement(). Recall that when a JSX element is compiled, it transforms into a React.createElement() call.

For this reason, you have to import the React library, and save it in a variable named React, before you can use any JSX at all. React.createElement() must be available in order for JSX to work. 

----------------------------
3.Import ReactDOM
---------------------------

    import ReactDOM from 'react-dom';
    
The methods imported from 'react-dom' are meant for interacting with the DOM. You are already familiar with one of them: ReactDOM.render().

The methods imported from 'react' don’t deal with the DOM at all. They don’t engage directly with anything that isn’t part of React.

To clarify: the DOM is used in React applications, but it isn’t part of React. After all, the DOM is also used in countless non-React applications. Methods imported from 'react' are only for pure React purposes, such as creating components or writing JSX elements.

-----------------------------
4.Create a Component Class
-----------------------------

You’ve learned that a React component is a small, reusable chunk of code that is responsible for one job, which often involves rendering HTML.

Here’s another fact about components: we can use a JavaScript class to define a new React component. We can also define components with JavaScript functions, but we’ll focus on class components first.

All class components will have some methods and properties in common (more on this later). Rather than rewriting those same properties over and over again every time, we extend the Component class from the React library. This way, we can use code that we import from the React library, without having to write it over and over again ourselves.

After we define our class component, we can use it to render as many instances of that component as we want.

What is React.Component, and how do you use it to make a component class?

React.Component is a JavaScript class. To create your own component class, you must subclass React.Component. You can do this by using the syntax class YourComponentNameGoesHere extends React.Component {}.

JavaScript classes and subclassing are a complex topic beyond the scope of this course. If you aren’t comfortable with them, here are some good resources to consult: 1 2 3 4.

Look at the code in app.js. A lot of it is still unfamiliar, but you can understand more than you could before!

On line 4, you know that you are declaring a new component class, which is like a factory for building React components. You know that React.Component is a class, which you must subclass in order to create a component class of your own. You also know that React.Component is a property on the object which was returned by import React from 'react' on line 1.

---------------------------
5.Name a Component Class
----------------------------

Good! Subclassing (React.Component) is the way to declare a new component class.

When you declare a new component class, you need to give that component class a name. On line 4, notice that our component class’s name is MyComponentClass.

Component class variable names must begin with capital letters!

This adheres to JavaScript’s class syntax. It also adheres to a broader programming convention in which class names are written in UpperCamelCase.

--------------------------------
6.Component Class Instructions
-------------------------------

Something that we haven’t talked about yet is the body of your component class: the pair of curly braces after React.Component, and all of the code between those curly braces.

Like all JavaScript classes, this one needs a body. The body will act as a set of instructions, explaining to your component class how it should build a React component.

    {
      render() {
        return <h1>Hello world</h1>;
      }
    }
    
That doesn’t look like a set of instructions explaining how to build a React component! Yet that’s exactly what it is. Read ->

-------------------------
7.The Render Function
--------------------------

A component class is like a factory that builds components. It builds these components by consulting a set of instructions, which you must provide. Let’s talk about these instructions!

For starters, these instructions should take the form of a class declaration body. That means that they will be delimited by curly braces, like this:

    class ComponentFactory extends React.Component {
      // instructions go here, between the curly braces
    }

The instructions should be written in typical JavaScript ES2015 class syntax.

There is only one property that you have to include in your instructions: a render method.

A render method is a property whose name is render, and whose value is a function. The term “render method” can refer to the entire property, or to just the function part.

    class ComponentFactory extends React.Component {
      render() {}
    }

A render method must contain a return statement. Usually, this return statement returns a JSX expression:

    class ComponentFactory extends React.Component {
      render() {
        return <h1>Hello world</h1>;
      }
    }

Of course, none of this explains the point of a render method. All you know so far is that its name is render, it needs a return statement for some reason, and you have to include it in the body of your component class declaration. We’ll get to the ‘why’ of it soon!

------------------------------
8.Create a Component Instance
------------------------------

MyComponentClass is now a working component class! It’s ready to follow its instructions and make some React components.

So, let’s make a React component! It only takes one more line:

    <MyComponentClass />
    
To make a React component, you write a JSX element. Instead of naming your JSX element something like h1 or div like you’ve done before, give it the same name as a component class. Voilà, there’s your component instance!

JSX elements can be either HTML-like, or component instances. JSX uses capitalization to distinguish between the two! That is the React-specific reason why component class names must begin with capital letters. In a JSX element, that capitalized first letter says, “I will be a component instance and not an HTML tag.”

-------------------------------
9.Render A Component
----------------------------
You have learned that a component class needs a set of instructions, which tell the component class how to build components. When you make a new component class, these instructions are the body of your class declaration:

    class MyComponentClass extends React.Component
    { // everything in between these curly-braces is instructions for how to build components

      render() {
        return <h1>Hello world</h1>;
      }
    }

This class declaration results in a new component class, in this case named MyComponentClass. MyComponentClass has one method, named render. This all happens via standard JavaScript class syntax.

You haven’t learned how these instructions actually work to make components! When you make a component by using the expression <MyComponentClass />, what do these instructions do?

Whenever you make a component, that component inherits all of the methods of its component class. MyComponentClass has one method: MyComponentClass.render(). Therefore, <MyComponentClass /> also has a method named render.

You could make a million different <MyComponentClass /> instances, and each one would inherit this same exact render method.

This lesson’s final exercise is to render your component. In order to render a component, that component needs to have a method named render. Your component has this! It inherited a method named render from MyComponentClass.

Since your component has a render method, all that’s left to do is call it. This happens in a slightly unusual way.

To call a component’s render method, you pass that component to ReactDOM.render(). Notice your component, being passed as ReactDOM.render()‘s first argument:

    ReactDOM.render(
      <MyComponentClass />,
      document.getElementById('app')
    );

ReactDOM.render() will tell <MyComponentClass /> to call its render method.

<MyComponentClass /> will call its render method, which will return the JSX element <h1>Hello world</h1>. ReactDOM.render() will then take that resulting JSX element, and add it to the virtual DOM. This will make “Hello world” appear on the screen.


----------------------------------------------------------------------------------------------------------------------------------------------------------------
C.Components and Advanced JSX
----------------------------------------------------------------------------------------------------------------------------------------------------------------

----------------------------------
1.Use Multiline JSX in a Component
----------------------------------

In this lesson, you will learn some common ways that JSX and React components work together. You’ll get more comfortable with both JSX and components, while picking up some new tricks. 

Take a look at this HTML:

    <blockquote>
      <p>
        The world is full of objects, more or less interesting; I do not wish to add any more.
      </p>
      <cite>
        <a target="_blank"
          href="https://en.wikipedia.org/wiki/Douglas_Huebler">
          Douglas Huebler
        </a>
      </cite>
    </blockquote>
    
How might you make a React component that renders this HTML?

Select QuoteMaker.js to see one way of doing it.

The key thing to notice in QuoteMaker is the parentheses in the return statement, on lines 6 and 18. Until now, your render function return statements have looked like this, without any parentheses:

    return <h1>Hello world</h1>;

However, a multi-line JSX expression should always be wrapped in parentheses! That is why QuoteMaker‘s return statement has parentheses around it.

Example:

    import React from 'react';
    import ReactDOM from 'react-dom';

    class QuoteMaker extends React.Component {
      render() {
        return (
          <blockquote>
            <p>
              The world is full of objects, more or less interesting; I do not wish to add any more.
            </p>
            <cite>
              <a target="_blank"
                href="https://en.wikipedia.org/wiki/Douglas_Huebler">
                Douglas Huebler
              </a>
            </cite>
          </blockquote>
        );
      }
    };

    ReactDOM.render(
      <QuoteMaker />,
      document.getElementById('app')
    );
    
-----------------------------------------
2.Use a Variable Attribute in a Component
----------------------------------------
Take a look at this JavaScript object named redPanda:

    const redPanda = {
      src: 'https://upload.wikimedia.org/wikipedia/commons/b/b2/Endangered_Red_Panda.jpg',
      alt: 'Red Panda',
      width: '200px
    };

Redpanda.js: 

    import React from 'react';
    import ReactDOM from 'react-dom';

    const redPanda = {
      src: 'https://upload.wikimedia.org/wikipedia/commons/b/b2/Endangered_Red_Panda.jpg',
      alt: 'Red Panda',
      width:  '200px'
    };

    class RedPanda extends React.Component {
      render() {
        return (
          <div>
            <h1>Cute Red Panda</h1>
            <img 
              src={redPanda.src}
              alt={redPanda.alt}
              width={redPanda.width} />
          </div>
        );
      }
    }

    ReactDOM.render(
      <RedPanda />,
      document.getElementById('app')
    );

How could you render a React component, and get a picture with redPanda‘s properties?

see above RedPanda.js for one way to do it.

Note all of the curly-brace JavaScript injections inside of the render function! Lines 16, 17, and 18 all use JavaScript injections.

You can, and often will, inject JavaScript into JSX inside of a render function.

------------------------------------
3.Put Logic in a Render Function
------------------------------------

A render() function must have a return statement. However, that isn’t all that it can have.

A render() function can also be a fine place to put simple calculations that need to happen right before a component renders. Here’s an example of some calculations inside of a render function:

    class Random extends React.Component {
      render() {
        // First, some logic that must happen
        // before rendering:
        const n = Math.floor(Math.random() * 10 + 1);
        // Next, a return statement
        // using that logic:
        return <h1>The number is {n}!</h1>;
      }
    }

Watch out for this common mistake:

    class Random extends React.Component {
      // This should be in the render function:
      const n = Math.floor(Math.random() * 10 + 1);

      render() {
        return <h1>The number is {n}!</h1>;
      }
    };

In the above example, the line with the const n declaration will cause a syntax error, as is it should not be part of the class declaration itself, but should occur in a method like render().

Full example : 

    import React from 'react';
    import ReactDOM from 'react-dom';


    const friends = [
      {
        title: "Yummmmmmm",
        src: "https://content.codecademy.com/courses/React/react_photo-monkeyweirdo.jpg"
      },
      {
        title: "Hey Guys!  Wait Up!",
        src: "https://content.codecademy.com/courses/React/react_photo-earnestfrog.jpg"
      },
      {
        title: "Yikes",
        src: "https://content.codecademy.com/courses/React/react_photo-alpaca.jpg"
      }
    ];

    // New component class starts here:
    class Friend extends React.Component {
      render() {
        const friend = friends[0] || friends[1] || friends[2];
        return (
          <div>
            <h1>{friend.title}</h1>
            <img
              src={friend.src}
            />
          </div>
        );
      }
    }

    ReactDOM.render(
      <Friend />,
      document.getElementById('app')
    );
    
--------------------------------------------
4.Use a Conditional in a Render Function
----------------------------------------------
How might you use a conditional statement inside of a render() function?

See below code to see one way of doing it.

Notice that the if statement is located inside of the render function, but before the return statement. This is pretty much the only way that you will ever see an if statement used in a render function.

    import React from 'react';
    import ReactDOM from 'react-dom';

    const fiftyFifty = Math.random() < 0.5;

    // New component class starts here:
    class TonightsPlan extends React.Component {
      render() {
        if (fiftyFifty) {
          return <h1>Tonight I'm going out WOOO</h1>;
        } else {
          return <h1>Tonight I'm going to bed WOOO</h1>;
        }
      }
    }

    ReactDOM.render(
        <TonightsPlan />,
        document.getElementById('app')
    );
    
----------------------------
5.Use this in a Component
---------------------------
The word this gets used in React a lot!

You are especially likely to see this inside of the body of a component class declaration. Here’s an example:

    class IceCreamGuy extends React.Component {
      get food() {
        return 'ice cream';
      }

      render() {
        return <h1>I like {this.food}.</h1>;
      }
    }

In the code, what does this mean?

The simple answer is that this refers to an instance of IceCreamGuy. The less simple answer is that this refers to the object on which this‘s enclosing method, in this case .render(), is called. It is almost inevitable that this object will be an instance of IceCreamGuy, but technically it could be something else.

Let’s assume that this refers to an instance of your component class, as will be the case in all examples in this course. IceCreamGuy has two methods: .food and .render(). Since this will evaluate to an instance of IceCreamGuy, this.food will evaluate to a call of IceCreamGuy‘s .food method. This method will, in turn, evaluate to the string “ice cream.”

Why don’t you need parentheses after this.food? Shouldn’t it be this.food()?

You don’t need those parentheses because .food is a getter method. You can tell this from the get in the above class declaration body.

There’s nothing React-specific about getter methods, nor about this behaving in this way! However, in React you will see this used in this way almost constantly.

---------------------------------------
6.Use an Event Listener in a Component
--------------------------------------

Render functions often contain event listeners. Here’s an example of an event listener in a render function:

    render() {
      return (
        <div onHover={myFunc}>
        </div>
      );
    }

Recall that an event handler is a function that gets called in response to an event. In the above example, the event handler is myFunc().

In React, you define event handlers as methods on a component class. Like this:

    class MyClass extends React.Component {
      myFunc() {
        alert('Stop it.  Stop hovering.');
      }

      render() {
        return (
          <div onHover={this.myFunc}>
          </div>
        );
      }
    }

Notice that the component class has two methods: .myFunc() and .render(). .myFunc() is being used as an event handler. .myFunc() will be called any time that a user hovers over the rendered <div></div>.

----------------------------
project2-Authorization Form
----------------------------
Scenario:

A client just called you to say that they love their new website! There’s only one problem: they don’t like how their contact page displays their personal information for all to see.

They’ve asked you to hide their website’s contact page behind a password form. In this project, you’ll accomplish this by using a React component to set up a simple authorization layer.

Let’s get started!

(Check uploaded files for the code)

---------------------------------------------------------------------------------------------------------------------------------------------------------------
Components Render Other Components
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------
1.Components Interact
-----------------------

A React application can contain dozens, or even hundreds, of components.

Each component might be small and relatively unremarkable on its own. When combined, however, they can form enormous, fantastically complex ecosystems of information.

In other words, React apps are made out of components, but what makes React special isn’t components themselves. What makes React special is the ways in which components interact.

This unit is an introduction to components interacting.

-----------------------------------------
1.A Component in a Render Function
------------------------------------------
Here is a .render() method that returns an HTML-like JSX element:

    class Example extends React.Component {
      render() {
        return <h1>Hello world</h1>;
      }
    }

You’ve seen render methods return <div></div>s, <p></p>s, and <h1></h1>s, just like in the above example.

Render methods can also return another kind of JSX: component instances.

    class OMG extends React.Component {
      render() {
        return <h1>Whooaa!</h1>;
      }
    }

    class Crazy extends React.Component {
      render() {
        return <OMG />;
      }
    }

In the above example, Crazy‘s render method returns an instance of the OMG component class. You could say that Crazy renders an <OMG />.

-------------------------------------------
2.Apply a Component in a Render Function
------------------------------------------
This is new territory! You’ve never seen a component rendered by another component before.

You have seen a component rendered before, though, but not by another component. Instead, you’ve seen a component rendered by ReactDOM.render().

When a component renders another component, what happens is very similar to what happens when ReactDOM.render() renders a component.

----------------------------
3.Require A File
---------------------------

When you use React.js, every JavaScript file in your application is invisible to every other JavaScript file by default. ProfilePage.js and NavBar.js can’t see each other.

This is a problem!

On line 9, you just added an instance of the NavBar component class. But since you’re in ProfilePage.js, JavaScript has no idea what NavBar means.

If you want to use a variable that’s declared in a different file, such as NavBar, then you have to import the variable that you want. To import a variable, you can use an import statement:

    import { NavBar } from './NavBar.js';

We’ve used import before, but not like this! Notice the differences between the above line of code and this familiar line:

    import React from 'react';

The first important difference is the curly braces around NavBar. We’ll get to those soon!

The second important difference involves the contents of the string at the end of the statement: 'react' vs './NavBar.js'.

If you use an import statement, and the string at the end begins with either a dot or a slash, then import will treat that string as a filepath. import will follow that filepath, and import the file that it finds.

If your filepath doesn’t have a file extension, then “.js” is assumed. So the above example could be shortened:

    import { NavBar } from './NavBar';
    
---------------
5.export
---------------

Alright! You’ve learned how to use import to grab a variable from a file other than the file that is currently executing.

When you import a variable from a file that is not the current file, then an import statement isn’t quite enough. You also need an export statement, written in the other file, exporting the variable that you hope to grab.

export comes from ES6’s module system, just like import does. export and import are meant to be used together, and you rarely see one without the other.

There are a few different ways to use export. In this course, we will be using a style called “named exports.” Here’s how named exports works:

In one file, place the keyword export immediately before something that you want to export. That something can be any top-level var, let, const, function, or class:

    // Manifestos.js:

    export const faveManifestos = {
      futurist: 'http://www.artype.de/Sammlung/pdf/russolo_noise.pdf',
      agile: 'https://agilemanifesto.org/iso/en/manifesto.html',
      cyborg:   'http://faculty.georgetown.edu/irvinem/theory/Haraway-CyborgManifesto-1.pdf'
    };

You can export multiple things from the same file:

    // Manifestos.js:
 
    export const faveManifestos = {
      futurist: 'http://www.artype.de/Sammlung/pdf/russolo_noise.pdf',
      agile:  'https://agilemanifesto.org/iso/en/manifesto.html',
      cyborg:   'http://faculty.georgetown.edu/irvinem/theory/Haraway-CyborgManifesto-1.pdf'
    };
 
    export const alsoRan = 'TimeCube';

In a different file, import the name of the var, let, const, function, or class from the first file:

    // App.js:

    // Import faveManifestos and alsoRan from ./Manifestos.js:
    import { faveManifestos, alsoRan } from './Manifestos';

    // Use faveManifestos:
    console.log(`A Cyborg Manifesto:  ${faveManifestos.cyborg}`); 

This style of importing and exporting in JavaScript is known as “named exports.” When you use named exports, you always need to wrap your imported names in curly braces, such as:

    import { faveManifestos, alsoRan } from './Manifestos';
    
Example:

NavBar.js

    import React from 'react';

    export class NavBar extends React.Component {
      render() {
        const pages = ['home', 'blog', 'pics', 'bio', 'art', 'shop', 'about', 'contact'];
        const navLinks = pages.map(page => {
          return (
            <a href={'/' + page}>
              {page}
            </a>
          )
        });

       return <nav>{navLinks}</nav>;
      }
    }

ProfilePage.js

    import React from 'react';
    import ReactDOM from 'react-dom';
    import {NavBar} from './NavBar';


    class ProfilePage extends React.Component {
      render() {
        return (
          <div>
            <NavBar />
            <h1>All About Me!</h1>
            <p>I like movies and blah blah blah blah blah</p>
            <img src="https://content.codecademy.com/courses/React/react_photo-monkeyselfie.jpg" />
          </div>
        );
      }
    }
    
    ReactDOM.render(
      <ProfilePage />,
      document.getElementById('app')
    );
    
    Output:
    
    home  blog  pics  bio  art  shop  about  contact
    
    All About Me!

    I like movies and blah blah blah blah blah
    
    Will be display Image
    
Congratulations! It may not seem like a big deal yet, but you’ve just discovered the key to React’s power.

By nesting components inside of other components, you can build infinitely complex architectures, even if each component is relatively simple. The relationship that you just built is the fundamental relationship of React.js.

---------------------------------------------------------------------------------------------------------------------------------------------------------
D.this.props
---------------------------------------------------------------------------------------------------------------------------------------------------------
Previously, you learned one way that components can interact: a component can render another component.

In this lesson, you will learn another way that components can interact: a component can pass information to another component.

Information that gets passed from one component to another is known as “props.”

Click Next to enter props-land!

------------------------------
2.Access a Component's props
--------------------------------
Every component has something called props.

A component’s props is an object. It holds information about that component.

To see a component’s props object, you use the expression this.props. Here’s an example of this.props being used inside of a render method:

    render() {
      console.log("Props object comin' up!");

      console.log(this.props);

      console.log("That was my props object!");

      return <h1>Hello world</h1>;
    }

Most of the information in this.props is pretty useless! But some of it is extremely important, as you’ll see.

----------------------------------------
3.Pass `props` to a Component
----------------------------------
You can pass information to a React component.

How? By giving that component an attribute:

    <MyComponent foo="bar" />

Let’s say that you want to pass a component the message, "This is some top secret info.". Here’s how you could do it:

    <Example message="This is some top secret info." />

As you can see, to pass information to a component, you need a name for the information that you want to pass.

In the above example, we used the name message. You can use any name you want.

If you want to pass information that isn’t a string, then wrap that information in curly braces. Here’s how you would pass an array:

    <Greeting myInfo={["top", "secret", "lol"]} />

In this next example, we pass several pieces of information to <Greeting />. The values that aren’t strings are wrapped in curly braces:

    <Greeting name="Frarthur" town="Flundon" age={2} haunted={false} />

-----------------------------------
4.Render a Component's props
------------------------------
You just passed information to a component’s props object!

You will often want a component to display the information that you pass.

Here’s how to make a component display passed-in information:

1 - Find the component class that is going to receive that information.
2 - Include this.props.name-of-information in that component class’s render method’s return statement.

Exa:

    import React from 'react';
    import ReactDOM from 'react-dom';

    class Greeting extends React.Component {
      render() {
        return <h1>Hi there, {this.props.firstName}!</h1>;
      }
    }

    ReactDOM.render(
      <Greeting firstName='meet' />, 
      document.getElementById('app')
    );
    
----------------------------------------
5.Pass props From Component To Component
----------------------------------------
You have learned how to pass a prop to a component:

    <Greeting firstName="Esmerelda" />

You have also learned how to access and display a passed-in prop:

    render() {
      return <h1>{this.props.firstName}</h1>;
    }

The most common use of props is to pass information to a component, from a different component. You haven’t done that yet, but it’s very similar to what you’ve seen already.

In this exercise, you will pass a prop from one component to another.

A curmudgeonly clarification about grammar:
You may have noticed some loose usage of the words prop and props. Unfortunately, this is pretty inevitable.

props is the name of the object that stores passed-in information. this.props refers to that storage object. At the same time, each piece of passed-in information is called a prop. This means that props could refer to two pieces of passed-in information, or it could refer to the object that stores those pieces of information :(

Ex:

    //Greeting.js
    import React from 'react';
    
    export class Greeting extends React.Component {
      render() {
        return <h1>Hi there, {this.props.name}!</h1>;
      }
    }
    
    //App.js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import {Greeting} from './Greeting.js';

    class App extends React.Component {
      render() {
        return (
          <div>
            <h1>
              Hullo and, "Welcome to The Newzz," "On Line!"
            </h1>
            <Greeting name="meet" />
            <article>
              Latest newzz:  where is my phone?
            </article>
          </div>
        );
      }
    }

    ReactDOM.render(
      <App />, 
      document.getElementById('app')
    );

------------------------------------
6.Render Different UI Based on props
----------------------------------
Awesome! You passed a prop from a component to a different component, accessed that prop from the receiver component, and rendered it!

You can do more with props than just display them. You can also use props to make decisions.

In the code editor, look at the Welcome component class.

You can tell from this.props.name on line 5 that Welcome expects to receive a piece of information called name. However, Welcome never renders this piece of information! Instead, it uses the information to make a decision.

<Welcome /> instances will render the text WELCOME "2" MY WEB SITE BABYYY!!!!!, unless the user is Mozart, in which case they will render the more respectful
hello sir it is truly great to meet you
here on the web.

The passed-in name is not displayed in either case! The name is used to decide what will be displayed. This is a common technique.

Select Home.js and look at the Home component class. What will <Welcome /> render to the screen?

    -----------------------------------
    //Welcome.js
    import React from 'react';

    export class Welcome extends React.Component {
      render() {
        if (this.props.name === 'Wolfgang Amadeus Mozart') {
          return (
            <h2>
              hello sir it is truly great to meet you here on the web
            </h2>
          );
        } else {
          return (
            <h2>
              WELCOME "2" MY WEB SITE BABYYY!!!!!
            </h2>
          );
        }
      }
    }
    -------------------------------------
    //Home.js
        import React from 'react';
    import ReactDOM from 'react-dom';
    import { Welcome } from './Welcome';

    class Home extends React.Component {
      render() {
        return <Welcome name='Ludwig van Beethoven' />;
      }
    }

    ReactDOM.render(
      <Home />, 
      document.getElementById('app')
    );
    --------------------------------------
    //Greeting.js
    import React from 'react';
    import ReactDOM from 'react-dom';

    export class Greeting extends React.Component {
      render() {
        if (this.props.signedIn === false) {
          return <h1>GO AWAY</h1>;
        } else {
          return <h1>Hi there, {this.props.name}!</h1>;
        }
      }
    }
    --------------------------------
    //App.js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import { Greeting } from './Greeting';

    class App extends React.Component {
      render() {
        return (
          <div>
            <h1>
              Hullo and, "Welcome to The Newzz," "On Line!"
            </h1>
            <Greeting name="Alison" signedIn={true} />
            <article>
              Latest:  where is my phone?
            </article>
          </div>
        );
      }
    }

    ReactDOM.render(
      <App />, 
      document.getElementById('app')
    );
    
    ----------------------
    Output: 
    
    Hullo and, "Welcome to The Newzz," "On Line!"
                Hi there, Alison!
            Latest: where is my phone?
            
--------------------------------------------
7.Put an Event Handler in a Component Class
--------------------------------------------
You can, and often will, pass functions as props. It is especially common to pass event handler functions.

In the next lesson, you will pass an event handler function as a prop. However, you have to define an event handler before you can pass one anywhere. In this lesson, you will define an event handler function.

How do you define an event handler in React?

You define an event handler as a method on the component class, just like the render method.

Take a look in the code editor. On lines 4 through 8, an event handler method is defined, with similar syntax as the render method. On line 12, that event handler method is attached to an event (a click event, in this case).

    //Example.js
    import React from 'react';

    class Example extends React.Component {
      handleEvent() {
        alert(`I am an event handler.
          If you see this message,
          then I have been called.`);
      }

      render() {
        return (
          <h1 onClick={this.handleEvent}>
            Hello world
          </h1>
        );
      }
    }
    
----------------------------------
8.Pass an Event Handler as a prop
------------------------------------
Good! You’ve defined a new method on the Talker component class. Now you’re ready to pass that function to another component.

You can pass a method in the exact same way that you pass any other information. Behold, the mighty JavaScript.

Select Talker.js.

You want to pass talk from here to <Button />.

If you want to pass any prop to <Button />, that means that you need to give <Button /> an attribute. Let’s start there.

Inside of Talker‘s render method, give <Button /> the following attribute:

    foo="bar"

During the next two checkpoints, you’ll replace those values with the values that you need! Keep them as foo and "bar" for now.

Your goal is to pass talk from <Talker /> to <Button />.

What prop name should you choose?
-> Since you’re going to pass a function named talk, you might as well use talk as your name. Inside of the render method, change your attribute name from foo to talk.

Change talk="bar" to talk={this.talk}.

--------------------------------------------
9.Receive an Event Handler as a prop
-------------------------------------------
Receive an Event Handler as a prop

Great! You just passed a function from <Talker /> to <Button />.

In the code editor, select Button.js. Notice that Button renders a <button></button> element.

If a user clicks on this <button></button> element, then you want your passed-in talk function to get called.

That means that you need to attach talk to the <button></button> as an event handler.

How do you do that? The same way that you attach any event handler to a JSX element: you give that JSX element a special attribute. The attribute’s name should be something like onClick or onHover. The attribute’s value should be the event handler that you want to attach.

Ex:

In Button.js, add an onClick attribute to the render method’s <button></button>.

The onClick attribute’s value should be the passed-down talk function. Since you named your prop talk in the last exercise, you can access this prop via {this.props.talk}.

Click Run. Once the browser refreshes, click on the button. Ew, how annoying!

-----------------------------------------------
10.handleEvent, onEvent, and this.props.onEvent
------------------------------------------------

Let’s talk about naming things.

When you pass an event handler as a prop, as you just did, there are two names that you have to choose.

Both naming choices occur in the parent component class - that is, in the component class that defines the event handler and passes it.

The first name that you have to choose is the name of the event handler itself.

Look at Talker.js, lines 6 through 12. This is our event handler. We chose to name it talk.

The second name that you have to choose is the name of the prop that you will use to pass the event handler. This is the same thing as your attribute name.

For our prop name, we also chose talk, as shown on line 15:

    return <Button talk={this.talk} />;

These two names can be whatever you want. However, there is a naming convention that they often follow. You don’t have to follow this convention, but you should understand it when you see it.

Here’s how the naming convention works: first, think about what type of event you are listening for. In our example, the event type was “click.”

If you are listening for a “click” event, then you name your event handler handleClick. If you are listening for a “keyPress” event, then you name your event handler handleKeyPress:

    class MyClass extends React.Component {
      handleHover() {
        alert('I am an event handler.');
        alert('I will be called in response to "hover" events.');
      }
    }

Your prop name should be the word on, plus your event type. If you are listening for a “click” event, then you name your prop onClick. If you are listening for a “keyPress” event, then you name your prop onKeyPress:

    class MyClass extends React.Component {
      handleHover() {
        alert('I am an event handler.');
        alert('I will listen for a "hover" event.');
      }

      render() {
        return <Child onHover={this.handleHover} />;
      }
    }

Ex:

    //Talker.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';
    import { Button } from './Button';

    class Talker extends React.Component {
      handleClick() {
        let speech = '';
        for (let i = 0; i < 10000; i++) {
          speech += 'blah ';
        }
        alert(speech);
      }

      render() {
        return <Button onClick={this.handleClick} />;
      }
    }

    ReactDOM.render(
      <Talker />,
      document.getElementById('app')
    );
    
    //Button.js
    
    import React from 'react';
    
    export class Button extends React.Component {
      render() {
        return (
          <button onClick={this.props.onClick} >
            Click me!
          </button>
        );
      }
    }
   
------------------   
Note !!!!!!!!!! :
-------------------
One major source of confusion is the fact that names like onClick have special meaning, but only if they’re used on HTML-like elements.

Look at Button.js. When you give a <button></button> an attribute named onClick, then the name onClick has special meaning. As you’ve learned, this special onClick attribute creates an event listener, listening for clicks on the <button></button>:

    // Button.js

    // The attribute name onClick
    // creates an event listner:
    <button onClick={this.props.onClick}>
      Click me!
    </button>

Now look at Talker.js. Here, when you give <Button /> an attribute named onClick, then the name onClick doesn’t do anything special. The name onClick does not create an event listener when used on <Button /> - it’s just an arbitrary attribute name:

    // Talker.js

    // The attribute name onClick
    // is just a normal attribute name:
    <Button onClick={this.handleClick} />

The reason for this is that <Button /> is not an HTML-like JSX element; it’s a component instance.

Names like onClick only create event listeners if they’re used on HTML-like JSX elements. Otherwise, they’re just ordinary prop names.

------------------------
11.this.props.children
--------------------------
Every component’s props object has a property named children.

this.props.children will return everything in between a component’s opening and closing JSX tags.

So far, all of the components that you’ve seen have been self-closing tags, such as <MyComponentClass />. They don’t have to be! You could write <MyComponentClass></MyComponentClass>, and it would still work.

this.props.children would return everything in between <MyComponentClass> and </MyComponentClass>.

Look at BigButton.js. In Example 1, <BigButton>‘s this.props.children would equal the text, “I am a child of BigButton.”

In Example 2, <BigButton>‘s this.props.children would equal a <LilButton /> component.

In Example 3, <BigButton>‘s this.props.children would equal undefined.

If a component has more than one child between its JSX tags, then this.props.children will return those children in an array. However, if a component has only one child, then this.props.children will return the single child, not wrapped in an array.

Ex:

    //App.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';
    import { List } from './List';

    class App extends React.Component {
      render() {
        return (
          <div>
            <List type='Living Musician'>
              <li>Sachiko M</li>
              <li>Harvey Sid Fisher</li>
            </List>
            <List type='Living Cat Musician'>
              <li>Nora the Piano Cat</li>
            </List>
          </div>
        );
      }
    }

    ReactDOM.render(
      <App />, 
      document.getElementById('app')
    );

    //List.js
    
    import React from 'react';

    export class List extends React.Component {
      render() {
        let titleText = `Favorite ${this.props.type}`;
        if (this.props.children instanceof Array) {
            titleText += 's';
        }
        return (
          <div>
            <h1>{titleText}</h1>
            <ul>{this.props.children}</ul>
          </div>
        );
      }
    }

-------------------------
12.defaultProps
------------------
Take a look at the Button component class.

Notice that on line 8, Button expects to receive a prop named text. The received text will be displayed inside of a <button></button> element.

What if nobody passes any text to Button?

If nobody passes any text to Button, then Button‘s display will be blank. It would be better if Button could display a default message instead.

You can make this happen by giving your component class a property named defaultProps:

    class Example extends React.Component {
      render() {
        return <h1>{this.props.text}</h1>;
      }
    }

    Example.defaultProps;

The defaultProps property should be equal to an object:

    class Example extends React.Component {
      render() {
        return <h1>{this.props.text}</h1>;
      }
    }
 
    // Set defaultProps equal to an object:
    Example.defaultProps = {};

Inside of this object, write properties for any default props that you’d like to set:

    class Example extends React.Component {
      render() {
        return <h1>{this.props.text}</h1>;
      }
    }

    Example.defaultProps = { text: 'yo' }; 

If an <Example /> doesn’t get passed any text, then it will display “yo.”

If an <Example /> does get passed some text, then it will display that passed-in text.

--------------------------------------------------------------------------------------------------------------------------------------------------------------
E.this.state
------------------------------------------------------------------------------------------------------------------------------------------------------------

----------
1.State
------------
Dynamic information is information that can change.

React components will often need dynamic information in order to render. For example, imagine a component that displays the score of a basketball game. The score of the game might change over time, meaning that the score is dynamic. Our component will have to know the score, a piece of dynamic information, in order to render in a useful way.

There are two ways for a component to get dynamic information: props and state. Besides props and state, every value used in a component should always stay exactly the same.

You just spent a long lesson learning about props. Now it’s time to learn about state. props and state are all that you need to set up an ecosystem of interacting React components.

------------------------
2.Setting Initial State
-----------------------
A React component can access dynamic information in two ways: props and state.

Unlike props, a component’s state is not passed in from the outside. A component decides its own state.

To make a component have state, give the component a state property. This property should be declared inside of a constructor method, like this:

    class Example extends React.Component {
      constructor(props) {
        super(props);
        this.state = { mood: 'decent' };
      }

      render() {
        return <div></div>;
      }
    }

    <Example />

Whoa, a constructor method? super(props)? What’s going on here? Let’s look more closely at this potentially unfamiliar code:

    constructor(props) {
      super(props);
      this.state = { mood: 'decent' };
    }

this.state should be equal to an object, like in the example above. This object represents the initial “state” of any component instance. We’ll explain that more soon!

How about the rest of the code? constructor and super are both features of ES6, not unique to React. There is nothing particularly React-y about their usage here. It is important to note that React components always have to call super in their constructors to be set up properly.

Look at the bottom of the highest code example in this column. <Example /> has a state, and its state is equal to { mood: 'decent' }.

-----------------------------
3.Access a Component's state
-----------------------------
To read a component’s state, use the expression (this.state.name-of-property) :

    class TodayImFeeling extends React.Component {
      constructor(props) {
        super(props);
        this.state = { mood: 'decent' };
      }

      render() {
        return (
          <h1>
            I'm feeling {this.state.mood}!
          </h1>
        );
      }
    }
    
----------------------------------
4.Update state with this.setState
---------------------------------
Look at..

    //Example.js
    import React from 'react';

    class Example extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          mood:   'great',
          hungry: false
        };
      }

      render() {
        return <div></div>;
      }
    }

    <Example />
    
A component can do more than just read its own state. A component can also change its own state.

A component changes its state by calling the function this.setState().

this.setState() takes two arguments: an object that will update the component’s state, and a callback. You basically never need the callback.

In the code editor, take a look at Example.js. Notice that <Example /> has a state of:

    {
      mood:   'great',
      hungry: false
    }

Now, let’s say that <Example /> were to call:

this.setState({ hungry: true });

After that call, here is what <Example />‘s state would be:

    {
      mood:   'great',
      hungry: true
    }

The mood part of the state remains unaffected!

this.setState() takes an object, and merges that object with the component’s current state. If there are properties in the current state that aren’t part of that object, then those properties remain how they were.

---------------------------------------------
5.Call this.setState from Another Function
-----------------------------------------------
The most common way to call this.setState() is to call a custom function that wraps a this.setState() call. .makeSomeFog() is an example:

class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = { weather: 'sunny' };
    this.makeSomeFog = this.makeSomeFog.bind(this);
  }
 
  makeSomeFog() {
    this.setState({
      weather: 'foggy'
    });
  }
}

Notice how the method makeSomeFog() contains a call to this.setState().

You may have noticed a weird line in there:

    this.makeSomeFog = this.makeSomeFog.bind(this);

This line is necessary because makeSomeFog()‘s body contains the word this. We’ll talk about it more soon!

Let’s walk through how a function wrapping this.setState() might work in practice. In the code editor, read Mood.js all the way through.

    //Mood.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';

    class Mood extends React.Component {
      constructor(props) {
        super(props);
        this.state = { mood: 'good' };
        this.toggleMood = this.toggleMood.bind(this);
      }

      toggleMood() {
        const newMood = this.state.mood == 'good' ? 'bad' : 'good';
        this.setState({ mood: newMood });
      }

      render() {
        return (
          <div>
            <h1>I'm feeling {this.state.mood}!</h1>
            <button onClick={this.toggleMood}>
              Click Me
            </button>
          </div>
        );
      }
    }

    ReactDOM.render(<Mood />, document.getElementById('app'));

Here is how a <Mood />‘s state would be set:

    1.A user triggers an event (in this case a click event, triggered by clicking on a <button></button>).

    2.The event from Step 1 is being listened for (in this case by the onClick attribute on line 20).

    3.When this listened-for event occurs, it calls an event handler function (in this case, this.toggleMood(), called on line 20 and defined on lines 11-14).

    4.Inside of the body of the event handler, this.setState() is called (in this case on line 13).

    5.The component’s state is changed!

Due to the way that event handlers are bound in JavaScript, this.toggleMood() loses its this when it is used on line 20. Therefore, the expressions this.state.mood and this.setState on lines 7 and 8 won’t mean what they’re supposed to… unless you have already bound the correct this to this.toggleMood.

That is why we must bind this.toggleMood to this on line 8.

For the less curious, just know that in React, whenever you define an event handler that uses this, you need to add this.methodName = this.methodName.bind(this) to your constructor function.

Look at the statement on line 12. What does that do?

Line 12 declares a const named newMood equal to the opposite of this.state.mood. If this.state.mood is “good”, then newMood will be “bad,” and vice versa.

A <Mood /> instance would display “I’m feeling good!” along with a button. Clicking on the button would change the display to “I’m feeling bad!” Clicking again would change back to “I’m feeling good!”, etc. Try to follow the step-by-step walkthrough in Mood.js and see how all of this works.

One final note: you can’t call this.setState() from inside of the render function! We’ll explain why in the next exercise.

---------------------------------------------
6.this.setState Automatically Calls render
---------------------------------------------
There’s something odd about all of this.

Look again at Toggle.js.

    //Toggle.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';

    const green = '#39D1B4';
    const yellow = '#FFD712';

    class Toggle extends React.Component {
      constructor(props){
        super(props);
        this.state = { color: green };
        this.changeColor = this.changeColor.bind(this);
      }

      changeColor() {
        const newColor = this.state.color == green ? yellow : green;
        this.setState({ color: newColor });
      }

      render() {
        return (
          <div style={{background: this.state.color}}>
            <h1>
              Change my color
            </h1>
            <button onClick={this.changeColor}>
                    Change colorthis.setState Automatically Calls render
                    </button>
          </div>
        );
      }
    }

    ReactDOM.render(<Toggle />, document.getElementById('app'));

When a user clicks on the <button></button>, the .changeColor() method is called. Take a look at .changeColor()‘s definition.

.changeColor() calls this.setState(), which updates this.state.color. However, even if this.state.color is updated from green to yellow, that alone shouldn’t be enough to make the screen’s color change!

The screen’s color doesn’t change until Toggle renders.

Inside of the render function, it’s this line:

    <div style={{background:this.state.color}}>

that changes a virtual DOM object’s color to the new this.state.color, eventually causing a change in the screen.

If you call .changeColor(), shouldn’t you then also have to call .render() again? .changeColor() only makes it so that, the next time that you render, the color will be different. Why can you see the new background right away, if you haven’t re-rendered the component?

Here’s why: Any time that you call this.setState(), this.setState() AUTOMATICALLY calls .render() as soon as the state has changed.

Think of this.setState() as actually being two things: this.setState(), immediately followed by .render().

That is why you can’t call this.setState() from inside of the .render() method! this.setState() automatically calls .render(). If .render() calls this.setState(), then an infinite loop is created.

----------------------------------------------------------------------------------------------------------------------------------------------------------
project3.Random Color Picker
----------------------------------------------------------------------------------------------------------------------------------------------------------
In this project, we’ll build a program that helps designers think of new color schemes.

Our program will set the screen’s background to a random color. Clicking a button will refresh to a new, random color. Random generators are a well-known tool for breaking a creative rut.

Let’s get started! 

Check Random.js & Button.js uploaded files.

----------------------------------------------------------------------------------------------------------------------------------------------------------
F.Component Lifecycle Methods
----------------------------------------------------------------------------------------------------------------------------------------------------------

We’ve seen that React components can be highly dynamic. They get created, rendered, added to the DOM, updated, and removed. All of these steps are part of a component’s lifecycle.

The component lifecycle has three high-level parts:

    1. Mounting, when the component is being initialized and put into the DOM for the first time
    2. Updating, when the component updates as a result of changed state or changed props
    3. Unmounting, when the component is being removed from the DOM

Every React component you’ve ever interacted with does the first step at a minimum. If a component never mounted, you’d never see it!

Most interesting components are updated at some point. A purely static component—like, for example, a logo—might not ever update. But if a component’s state changes, it updates. Or if different props are passed to a component, it updates.

Finally, a component is unmounted when it’s removed from the DOM. For example, if you have a button that hides a component, chances are that component will be unmounted. If your app has multiple screens, it’s likely that each screen (and all of its child components) will be unmounted. If a component is “alive” for the entire lifetime of your app (say, a top-level <App /> component or a persistent navigation bar), it won’t be unmounted. But most components can get unmounted one way or another!

It’s worth noting that each component instance has its own lifecycle. For example, if you have 3 buttons on a page, then there are 3 component instances, each with its own lifecycle. However, once a component instance is unmounted, that’s it—it will never be re-mounted, or updated again, or unmounted.

---------------------------------------
2.Introduction to Lifecycle Methods
------------------------------------

React components have several methods, called lifecycle methods, that are called at different parts of a component’s lifecycle. This is how you, the programmer, deal with the lifecycle of a component.

You may not have known it, but you’ve already used two of the most common lifecycle methods: constructor() and render()! constructor() is the first method called during the mounting phase. render() is called later during the mounting phase, to render the component for the first time, and during the updating phase, to re-render the component.

Notice that lifecycle methods don’t necessarily correspond one-to-one with part of the lifecycle. constructor() only executes during the mounting phase, but render() executes during both the mounting and updating phase.

With this new understanding, let’s build a simple clock component.

    //Clock.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';

    class Clock extends React.Component {
      // Add your methods in here.
      constructor(props){
        super(props);
        this.state = { date: new Date() };
      }
      render(){
            return <div>{this.state.date.toLocaleTimeString()}</div>;
      }

    }

    ReactDOM.render(<Clock />, document.getElementById('app'));
    
    //output
    
    12:50:47 PM - (current time)
    
(Remember: the constructor is the first thing called when the component instance is mounted.)

(Remember: the constructor is the first thing called during mounting. render() is called later, to show the component for the first time. If it happened in a different order, render() wouldn’t have access to this.state, and it wouldn’t work.)

-----------------------------------
3.componentDidMount
----------------------------------
We’ve made a clock component, but it’s static. Wouldn’t it be nice if it updated?

At a high level, we’d like to update this.state.date with a new date once per second.

JavaScript has a helpful function, setInterval(), that will help us do just this. It lets us run a function on a set interval. In our case, we’ll make a function that updates this.state.date, and call it every second.

We’ll want to run some code that looks like this:

    // NOTE: This code doesn't clean itself up properly.
    // We'll explore that in the next exercise.
    const oneSecond = 1000;
    setInterval(() => {
      this.setState({ date: new Date() });
    }, oneSecond);

We have the code we want to run—that’s great. But where should we put this code? In other words, where in the component’s lifecycle should it go?

Remember, the component lifecycle has three high-level parts:

    1. Mounting, when the component is being initialized and put into the DOM for the first time
    2. Updating, when the component updates as a result of changed state or changed props
    3. Unmounting, when the component is being removed from the DOM

It’s certainly not in the unmounting phase—we don’t want to start our interval when the clock disappears from the screen! It’s also probably not useful during the updating phase—we want the interval to start as soon as the clock appears, and we don’t want to wait for an update. It probably makes sense to stick this code somewhere in the mounting phase.

We’ve seen two functions: the render() and the constructor. Can we put this code in either of those places?

render() isn’t a good candidate. For one, it executes during the mounting phase and the updating phase—too often for us. It’s also generally a bad idea to set up any kind of side-effect like this in render(), as it can create subtle bugs in the future.

constructor() is also not great. It does only execute during the mounting phase, so that’s good, but you should generally avoid side-effects like this in constructors because it violates something called the Single Responsibility Principle. In short, it’s not a constructor’s responsibility to start side-effects. (You can read more about the principle on Wikipedia.)

If it’s not render() or the constructor, then where? Enter a new lifecycle method, componentDidMount().

componentDidMount() is the final method called during the mounting phase. The order is:

    1. The constructor
    2. render()
    3. componentDidMount()

In other words, it’s called after the component is rendered. This is where we’ll want to start our timer.

(Another method, getDerivedStateFromProps(), is called between the constructor and render(), but it is very rarely used and usually isn’t the best way to achieve your goals. We won’t be talking about it in this lesson.)

    //Clock.js
    
    import React from 'react';
    import ReactDOM from 'react-dom';

    class Clock extends React.Component {
      constructor(props) {
        super(props);
        this.state = { date: new Date() };
      }
      render() {
        return <div>{this.state.date.toLocaleTimeString()}</div>;
      }
      componentDidMount() {
        // Paste your code here.
        const oneSecond = 1000;
        setInterval(() => {
          this.setState({ date: new Date() });
        }, oneSecond);
      }
    }

    ReactDOM.render(<Clock />, document.getElementById('app'));
    
    Output:
    
    Every one second time will be updated.

------------------------------------
4.componentWillUnmount
------------------------------------
Our clock is working, but it has an important problem. We never told the interval to stop, so it’ll keep running that function forever (or at least, until the user leaves/refreshes the page).

When the component is unmounted (in other words, removed from the page), that timer will keep on ticking, trying to update the state of a component that’s effectively gone. This means your users will have some JavaScript code running unnecessarily, which will hurt the performance of your app.

React will log a warning that looks something like this:

Warning: Can't perform a React state update on an unmounted component. This is a no-op, but it indicates a memory leak in your application. To fix, cancel all subscriptions and asynchronous tasks in the componentWillUnmount method.

Imagine if the clock gets mounted and unmounted hundreds of times—eventually, this will cause your page to become sluggish because of all of the unnecessary work. You’ll also see warnings in your browser console. Even worse, this can lead to subtle, annoying bugs.

All this bad stuff can happen if we fail to clean up a side-effect of a component. In our case this is a call to setInterval(), but components can have lots of other side-effects: loading external data with AJAX, doing manual tweaking of the DOM, setting a global value, and more. We try to limit our side-effects, but it’s difficult to build an interesting app with truly zero side-effects.

In general, when a component produces a side-effect, you should remember to clean it up.

JavaScript gives us the clearInterval() function. setInterval() can return an ID, which you can then pass into clearInterval() to clear it. Here’s the code we’ll want to use:

    const oneSecond = 1000;
    this.intervalID = setInterval(() => {
      this.setState({ date: new Date() });
    }, oneSecond);

    // Some time later...
    clearInterval(this.intervalID);

At a high level, we want to continue to set up our setInterval() in componentDidMount(), but then we want to clear that interval when the clock is unmounted.

Let’s introduce a new lifecycle method: componentWillUnmount(). componentWillUnmount() is called in the unmounting phase, right before the component is completely destroyed. It’s a useful time to clean up any of your component’s mess.

In our case, we’ll use it to clean up the clock’s interval.

    //Clock.js
    
    import React from 'react';

    export class Clock extends React.Component {
      constructor(props) {
        super(props);
        this.state = { date: new Date() };
      }
      render() {
        return <div>{this.state.date.toLocaleTimeString()}</div>;
      }
      componentDidMount() {
        const oneSecond = 1000;
        this.intervalID = setInterval(() => {
          this.setState({ date: new Date() });
        }, oneSecond);
      }
      componentWillUnmount() {
        clearInterval(this.intervalID)
      }
    }

-----------------------------------------
5.componentDidUpdate
--------------------------------
Remember the three parts of a component’s lifecycle:

    1. Mounting, when the component is being initialized and put into the DOM for the first time
    2. Updating, when the component updates as a result of changed state or changed props
    3. Unmounting, when the component is being removed from the DOM

We’ve looked at mounting (constructor(), render(), and componentDidMount()). We’ve looked at unmounting (componentWillUnmount()). Let’s finish by looking at the updating phase.

An update is caused by changes to props or state. You’ve already seen this happen a bunch of times. Every time you’ve called setState() with new data, you’ve triggered an update. Every time you change the props passed to a component, you’ve caused it to update.

When a component updates, it calls several methods, but only two are commonly used.

The first is render(), which we’ve seen in every React component. When a component’s props or state changes, render() is called.

The second, which we haven’t seen yet, is componentDidUpdate(). Just like componentDidMount() is a good place for mount-phase setup, componentDidUpdate() is a good place for update-phase work.

    //Clock.js
    
    import React from 'react';

    export class Clock extends React.Component {
      constructor(props) {
        super(props);
        this.state = { date: new Date() };
      }
      render() {
        return (
          <div>
            {this.props.isPrecise
              ? this.state.date.toISOString()
              : this.state.date.toLocaleTimeString()}
          </div>
        );
      }
      startInterval() {
        let delay;
        if (this.props.isPrecise) {
          delay = 100;
        } else {
          delay = 1000;
        }
        this.intervalID = setInterval(() => {
          this.setState({ date: new Date() });
        }, delay);
      }
      componentDidMount() {
        this.startInterval();
      }
      componentDidUpdate(prevProps) {
        if (this.props.isPrecise === prevProps.isPrecise) {
          return;
        }
        clearInterval(this.intervalID);
        this.startInterval();
      }
      componentWillUnmount() {
        clearInterval(this.intervalID);
      }
    }

----------------------------------------
project4.Social Network for Pets
------------------------------------------
In this project, we’ll build a simple social network for pets. You’ll be able to view a pet’s profile (which contains their name, bio, and friend list) and navigate to other profiles. There will also be a profile directory where you can see all of the profiles.

We’ve already set up three profiles for you: one for a cat, one for a dog, and one for a Komodo dragon.

Let’s get started!

Check repository for code.

-----------------------------------
G.Stateless Functional Components
-----------------------------------

--------------------------------------
1.Stateless Functional Components
-------------------------------------

In the code editor, take a look at Example.js. The first Example component is defined as a JavaScript class, but it doesn’t have to be! In React, we can also define components as JavaScript functions — we call them function components to differentiate them from class components.

In the latest versions of React, function components can do everything that class components can do. They have analogous features for props, state, and lifecycle methods. This lesson will focus on converting a class component to a function component and adding props, which are available in all versions of React.

Compare the Example class component and the Example function component. For the most basic function components, all you need to do is remove the beginning render() { and ending } of the render() method:

    render() { // Delete this
      return <h1>Hello</h1>
    } // Delete this

To put it in other words: the function component should return the same JSX that was originally returned by the render() method.

Ex:

    // A component class written in the usual way:
    export class MyComponentClass extends React.Component {
      render() {
        return <h1>Hello world</h1>;
      }
    }

    // The same component class, written as a stateless functional component:
    export const MyComponentClass = () => {
      return <h1>Hello world</h1>;
    }

    // Works the same either way:
    ReactDOM.render(
        <MyComponentClass />,
        document.getElementById('app')
    );
    
--------------------------------
2.Function Components and Props
--------------------------------
Like any component, function components can receive information via props.

To access these props, give your function component a parameter named props. Within the function body, you can access the props using this pattern: props.propertyName. You don’t need to use the this keyword.

    export function YesNoQuestion (props) {
      return (
        <div>
          <p>{props.prompt}</p>
          <input value="Yes" />
          <input value="No" />
        </div>
      );
    }

    ReactDOM.render(
      <YesNoQuestion prompt="Have you eaten an apple today?" />,
      document.getElementById('app');
    );

In the above example, we pass a value of “Have you eaten an apple today?” as the prompt prop when rendering YesNoQuestion.

Quick Review:

Well done! You’ve written your first function component. Here’s a recap:

1.Function components are React components defined as JavaScript functions.

2.Function components must return JSX.

3.Function components may accept a props parameter. Expect it to be a JavaScript object.

Although function components and class components can do the same things, you’ll see a lot of function components in the React documentation and example apps. Some developers prefer them over class components for their simplicity and straightforward features, like Hooks, which you’ll learn later in your coding journey.
