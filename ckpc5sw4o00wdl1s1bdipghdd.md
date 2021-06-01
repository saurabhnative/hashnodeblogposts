## Fundamentals of Javascript - Part 2(Why should you use let instead of var keyword)

Hello, curious stranger on the internet, today we are going to cover why `let` and `const` keyword is preferred over `var` keyword in Javascript.

In the  [first part](https://saurabhnative.hashnode.dev/fundamentals-of-javascript-part-1)  of fundamentals of Javascript, we covered features of Javascript and how to declare variables using `let` and `const` keywords.

Let's continue our journey to deep dive into the Javascript world from that point.

**The `var` keyword**
In addition to declaring variables using `let` and `const`, there is another way to declare variables using the `var` keyword.
A variable can be declared using the `var` keyword as shown below:-
```
var studentName = "Joe";
console.log("Student name is", studentName);

//Output:- Student name is Joe
``` 

However, using the `let` and `const` keyword is much more preferable to using the `var` keyword in Javascript. One of the reasons for this is because variable declared using the `var` keyword can be redeclared using the same name which can lead to a lot of bugs in the code.
Consider the example below:-

```
var studentName = "Joe";
console.log("Student name is", studentName);
var studentName = "John";
console.log("Student name now is", studentName);

/* Output:-
Student name is Joe
Student name now is John
*/
```
In the above example, the `studentName` variable was declared again with a new value without any error. This can lead to bugs while coding. For example, if a person `x` is using the `studentName` variable in their file and a person `y` is using the same variable `studentName` in their code. The value of the `studentName` variable will not remain deterministic and can have incorrect values during final program execution.

If we try to do a similar thing with the `let` keyword this will be the output:-

```
let studentName = "Joe";
console.log("Student name is", studentName);
let studentName = "John";
console.log("Student name now is", studentName);

/*Output:-
SyntaxError: Identifier 'studentName' has already been declared
*/
```

In the case of the `let` keyword, reuse of the same variable name again is not allowed due to which each variable used in the code has a deterministic value. This prevents any unnecessary bugs to enter into our code.

This is one of the reasons why we make use of the `let` or `const` keyword instead of the `var` keyword in Javascript currently.

We will continue learning more about Javascript language in the upcoming articles in the series. I hope you found the article useful.   
Which is your favourite feature of Javascript language? Do share it in the comments below.    
I create content about building web applications and general programming. If this is something that interests you, please share the article with your friends and connections. You can also subscribe to my newsletter to get updates every time I write something!

Thank you for reading, If you have reached so far, please like the article, It will encourage me to write more such articles. Do share your valuable suggestions, I appreciate your honest feedback!

I would love to connect with you on [Twitter](https://twitter.com/saurabhnative) | [Instagram](https://www.instagram.com/saurabhnative).

You should definitely check out my other Blogs:

- [Fundamentals of Javascript - Part 1](https://saurabhnative.hashnode.dev/fundamentals-of-javascript-part-1)

- [Solving LeetCode array problems using Javascript - Part 1](https://coderwhodreams.hashnode.dev/solving-leetcode-array-problems-using-javascript-part-1)

- [Learn how to build Christmas greeting using CSS Animations](https://coderwhodreams.hashnode.dev/learn-how-to-build-christmas-greeting-using-css-animations)

See you in my next article, Take care!!

