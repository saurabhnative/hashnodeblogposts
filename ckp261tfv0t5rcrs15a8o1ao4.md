## Fundamentals of Javascript - Part 1

Hello, curious stranger on the internet, have you ever struggled with learn the core concepts of Javascript and could not find the right resources to learn it easily?
Today, I will solve this problem for you by explaining these concepts in the easiest possible manner.
The agenda of the article will be:
   - Features of Javascript
   - Learning how to print statements and add comments
   - How to declare variables using `let` and `const`

Before we begin the actual coding parts, let's understand a few key features about Javascript itself:-

**Javascript is an interpreted language.**     
All of the programming languages in the world can be classified into two categories viz. Compiled Languages and Interpreted Languages.
In a compiled language, we build a compiled code from the program using a compiler and the target machine directly runs the compiled program. 
In an interpreted language, the program is not compiled and directly translated by the target machine. Instead, a different program, aka the interpreter, reads the code line by line and executes the code in real-time.

For example, let's say you are trying to make Dalgona coffee at home. But the recipe shared by your friend is in ancient Latin. Since you don't know Latin, you can make coffee from the recipe using either of the two below approaches.
 
1. You will get the recipe translated into English using a translation service or program. Then you can use the English version of the recipe directly to make Dalgona coffee at home. This is similar to how you would run a program through a compilation service to get a compiled code that can be used directly by a machine to run a specific task.

2. The Second approach could be to search for a friend who knows ancient Latin, get him/her over to your house and ask him/her to translate the recipe line by line while you make the coffee. This is similar to how we use an interpreter to go through the program code line by line while executing a specific task. 

Javascript is an interpreted language and follows the second approach from the two approaches above to run your code. Note that interpreted languages are also called scripting languages sometimes.


![Screenshot 2021-05-23 at 5.54.12 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621772664269/GWjpU7fGx.png)

You can learn more about compiled and interpreted languages from the article below from which the above example is taken:-

https://www.freecodecamp.org/news/compiled-versus-interpreted-languages/

**Javascript is used for cross-platform application development** 


![Screenshot 2021-05-24 at 9.22.44 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621828386462/p9usApjUK.png)

Initially, javascript was used as a browser-only language. But in 2009,  [Node.js](https://nodejs.org/en/)  was introduced by Ryan Dahl for writing server-side code using Javascript. With this, it became possible for the developer community to develop the backend part of websites along with the frontend using Javascript.

In 2013, the  [React.js](https://reactjs.org/)  framework was introduced by Facebook to ease the website development process. React became a popular choice for the development of websites and soon efforts were made to use core parts of react library for mobile application development. In 2015, these efforts led to the creation of the  [ReactNative](https://reactnative.dev/)  framework which allowed usage of Javascript to develop mobile applications with near-native performance. Although hybrid frameworks like Cordova existed before Reactnative to develop mobile applications using Javascript, the ReactNative team brought a lot of performance improvements while using Javascript for mobile app development.
After the introduction of  [Electron.js](https://www.electronjs.org/), developers were also able to build desktop applications using Javascript.

All these libraries allowed developers to use a single language for developing a complete from end to end for different platforms. This is one of the major reasons why Javascript became so popular in the developer community.

We can now start learning the basic concepts of the Javascript programming language. Let's begin by printing a simple `Hello everyone` statement using Javascript.

I am currently using [Replit](https://replit.com/) for running javascript code snippets. It is an online browser-based code editor where we can run different programs easily. We are going to choose a Node.js based `repl` in the editor and continue with our coding part.

**Printing statements in Javascript**

If we want to print any sentence using Javascript language, we make use of the `console.log` statement. This will print the value in the browser console usually and in the current case in the console present on the right-hand side of the repl.

```javascript
console.log("Hello everyone");

// Console output: Hello everyone
```

In case you would like to include quote characters in the output, you can use the concept of  [escape characters](https://www.tutorialspoint.com/escape-characters-in-javascript) in Javascript as shown below:-

```javascript
console.log("\"Hello everyone\"");

// Console output: "Hello everyone"
```

**Comments in Javascript**

We can use `//` characters to add single line comment in Javascript as shown below:-

```javascript
// This is a single line comment
```

For multiline comments, we start the comment with `/*` and end the comment with `*/` as shown below:-

```
/*
This is a multiline comment
We can add multiple lines in the comment
*/
```

**Variable declaration in Javascript**

Variables are the names we give to computer memory locations in which store values for a specific purpose. 
We can declare variables in Javascript either using the `let` or `const` keyword.  
The declaration of a variable using the `let` keyword can be done as shown below:-

```javascript
let studentName = "Joe";
console.log("The name of my student is "+studentName);

//Output:- The name of my student is Joe
```
Note:- We can either use `+` symbol or `,` to combine text with a variable in javascript while printing the values.

We generally use the `let` keyword when there is a need to redefine or redeclare our variables. In simpler terms, if the value stored in a variable needs to change at some time in future in our program, we make use of the `let` keyword.
Let's learn this with an example:-
```javascript
let studentName = "Joe";
console.log("The name of my student is "+studentName);

studentName = "John";
console.log("The name of my student is "+studentName);

/* Output:- 
The name of my student is Joe
The name of my student is John
*/
```

Here we redefined the `studentName` variable to store a new value `John` after storing the initial value as `Joe`. In such cases, we make use of the `let` keyword.

`const` keyword is used when a variable needs to store a fixed value which never changes during entire program execution.  
Let's understand this with an example:-  

```javascript
const pi = 3.14;
console.log("Value of pi", pi);
```

When we define the value mathematical constant like `π` in our program, we know that its value will not change during the entire program execution. So we define the value using the `const` keyword.

In summary of today's article, we learnt of main features of the javascript language, how to print values, write comments and declare variables.

We will continue learning more about Javascript language in the upcoming articles in the series. I hope you found the article useful.   
Which is your favourite feature of Javascript language? Do share it in the comments below.    
I create content about building web applications and general programming. If this is something that interests you, please share the article with your friends and connections. You can also subscribe to my newsletter to get updates every time I write something!

Thank you for reading, If you have reached so far, please like the article, It will encourage me to write more such articles. Do share your valuable suggestions, I appreciate your honest feedback!

I would love to connect with you on [Twitter](https://twitter.com/saurabhnative) | [Instagram](https://www.instagram.com/coder_who_dreams/).

You should definitely check out my other Blogs:

- [Popular frontend interview questions](https://coderwhodreams.hashnode.dev/popular-frontend-interview-questions-and-answers-part-1)

- [Solving LeetCode array problems using Javascript - Part 1](https://coderwhodreams.hashnode.dev/solving-leetcode-array-problems-using-javascript-part-1)

- [Learn how to build Christmas greeting using CSS Animations](https://coderwhodreams.hashnode.dev/learn-how-to-build-christmas-greeting-using-css-animations)

See you in my next article, Take care!!







