## Solving LeetCode array problems using Javascript Part 2

Hello, curious stranger on the internet, in today's post, we will solve a LeetCode array problem using Javascript. We are interested in solving is Valid Mountain Array problem from LeetCode mentioned below:-

https://leetcode.com/explore/learn/card/fun-with-arrays/527/searching-for-items-in-an-array/3251/

For this problem, we need to first understand what is a mountain exactly. 

A given array is a mountain array if and only if:
 1. The length of an array is greater than 3
 2. There exists an element `i` in the array such that all elements before `i` are smaller than `i` and all elements after `i` are greater.

You can find an example of a mountain array below:-

![Screenshot 2021-05-21 at 10.40.28 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1621573836925/Pg5y-HsJf.png "example of mountain array problem")

In programming terms the condition could be stated as:-
An array is a mountain array if and only if:
```
arr.length >= 3
There exists some i with 0 < i < arr.length - 1 such that:
arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
```

We have been given a function called `validMountainArray` with an array as an input parameter. We are supposed to write code within the function. If the array is a mountain array we should return `true` else return `false`

Broadly the algorithm I have used to solve this is 
 1. First check if the length of the array is greater than 3
 2. Then find the max element in the array and check whether it is not the first or last element in the array. Since if it is the first or the last element, we cannot get an increasing followed by decreasing order of elements.
3. Check whether all the elements before the max element are in increasing order.
4. Check whether all the elements after the max element are in decreasing order.
5. If all these conditions are satisfied only then our array is a valid mountain array.

The first condition we can add is that if the length of the input array `arr` is less than 3 then return `false` since the array can't be mountain array in that case:-

```
const validMountainArray = function(arr) {
    if(arr.length<3) {
        return false;
    }
}
```

Next, we will write a for loop to find the index of the largest element in the array:-
```
const validMountainArray = function(arr) {
    if(arr.length<3) {
        return false;
    } else {
        let maxElementIndex = 0;
        // find max
        for(let i=1;i<arr.length;i++) {
            if(arr[i]>=arr[maxElementIndex]) {
                maxElementIndex = i;
            }
        }
   }
}
```

Now we add a check to see if the max element is not the first or last element by comparing the element index:-
```
...
        let maxElementIndex = 0;
        for(let i=1;i<arr.length;i++) {
            if(arr[i]>=arr[maxElementIndex]) {
                maxElementIndex = i;
            }
        }
        // check whether max element is not the first or last element
        if(maxElementIndex === arr.length-1 || maxElementIndex === 0) {
            return false;
        }
```

Next, we check whether elements before the largest element are in increasing order:-
```
....
       if(maxElementIndex === arr.length-1 || maxElementIndex === 0) {
            return false;
        }

        let isMountainArray = true;
        // check whether elements before the largest element are in increasing order
        for(let j=0;j<maxElementIndex;j++) {
            console.log("In j loop", arr[j], arr[j+1]);
            if(arr[j]>=arr[j+1]) {
                isMountainArray = false;
            }
        }
```

Lastly, we will check whether elements after the greatest element in decreasing order:-
```
        // check whether elements after the greatest element in decreasing order
        for(let k=maxElementIndex;k<arr.length-1;k++) {
            console.log("In k loop", arr[k], arr[k+1]);
            if(arr[k]<=arr[k+1]) {
                isMountainArray = false;
            }
        }

        return isMountainArray;
```

We have returned the `isMountainAraay` value in the last line.   
The complete solution for the problem is as shown below:-
```
const validMountainArray = function(arr) {
    if(arr.length<3) {
        return false;
    } else {
        let maxElementIndex = 0;
        for(let i=1;i<arr.length;i++) {
            if(arr[i]>=arr[maxElementIndex]) {
                maxElementIndex = i;
            }
        }
        
        if(maxElementIndex === arr.length-1 || maxElementIndex === 0) {
            return false;
        }

        let isMountainArray = true;

        for(let j=0;j<maxElementIndex;j++) {
            console.log("In j loop", arr[j], arr[j+1]);
            if(arr[j]>=arr[j+1]) {
                isMountainArray = false;
            }
        }

        for(let k=maxElementIndex;k<arr.length-1;k++) {
            console.log("In k loop", arr[k], arr[k+1]);
            if(arr[k]<=arr[k+1]) {
                isMountainArray = false;
            }
        }

        return isMountainArray;
    }
}; 
```

We will cover more such competitive programming problems in the upcoming articles in this series. I hope you found the article useful. Which is your favourite competitive programming data structure? Do share it in the comments below.    
I create content about Web Application tutorials and general programming. If this is something that interests you, please share the article with your friends and connections. You can also subscribe to my newsletter to get updates every time I write something!

Thank you for reading, If you have reached so far, please like the article, It will encourage me to write more such articles. Do share your valuable suggestions, I appreciate your honest feedback!

I would love to connect with you on [Twitter](https://twitter.com/saurabhnative) | [Instagram](https://www.instagram.com/coder_who_dreams/).

You should definitely check out my other Blogs:

- [Popular frontend interview questions](https://coderwhodreams.hashnode.dev/popular-frontend-interview-questions-and-answers-part-1)

- [Solving LeetCode array problems using Javascript - Part 1](https://coderwhodreams.hashnode.dev/solving-leetcode-array-problems-using-javascript-part-1)

- [Learn how to build Christmas greeting using CSS Animations](https://coderwhodreams.hashnode.dev/learn-how-to-build-christmas-greeting-using-css-animations)

See you in my next article, Take care!!
