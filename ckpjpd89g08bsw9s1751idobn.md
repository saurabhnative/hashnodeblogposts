## Solving LeetCode array problems using Javascript Part 3

Hello everyone, so I'm back with another leet code solutions tutorial and today we are going to solve another Leetcode array problem.   
The problem for the day is going to be to Replace Elements with Greatest Element on Right Side.

Problem link on leetcode:-
https://leetcode.com/explore/learn/card/fun-with-arrays/511/in-place-operations/3259/

So, just to give you a brief overview of how the problem goes by, we have an input array of elements. We have to replace every element in that array with the greatest element among the elements towards the right side and replace the last element with -1. 

When I first read these, I had no clue what was expected, but it became a lot clearer after going through the example.   

So let's say your input array. 
```
Input: arr = [17,18,5,4,6,1]
```
And you're supposed to use some kind of algorithm to solve this problem.

Now the way this problem goes by, we pick up each element for example let's say 17 and then we search for all the elements after that element index, that is we search on a subarray from element `18` to element `1`, and we try to find the greatest element.
 
Obviously, it is 18 Right. So then we replace the first element with 18 which is in place of element 17.
Once I'm done with that, my element at index `0` will be 18. After that, we move on to the second index. And here we again start searching for elements and repeat the process.
We need to replace the last element with -1 in the end.

The detailed explanation is as shown below:-

```
Explanation: 
Input: arr = [17,18,5,4,6,1]
- index 0 --> the greatest element to the right of index 0 is index 1 (18).
- index 1 --> the greatest element to the right of index 1 is index 4 (6).
- index 2 --> the greatest element to the right of index 2 is index 4 (6).
- index 3 --> the greatest element to the right of index 3 is index 4 (6).
- index 4 --> the greatest element to the right of index 4 is index 5 (1).
- index 5 --> there are no elements to the right of index 5, so we put -1.
Output: [18,6,6,6,1,-1]
```

So our job is first to replace each element at each index with the greatest element from the rest of the array. And when all the greatest elements are shifted towards the left, the last element is replaced by minus one. So that is how the problem is designed, or the problem is supposed to be solved.
Now we have some constraints here as well:-

1 <= arr.length <= 10<sup>4</sup>
  
1 <= arr[i] <= 10<sup>5</sup>


So array length can be of 10 to the power 4 and element can be till 10 to the power of 5.

So coming back to our language of choice we use JavaScript from the list of available languages to solve this problem.

So referring to the above example, let's try to come up with pseudocode. So, for the example, we know that we have to iterate the array at least once. Why? Because we need to pick our element at a particular index, and then go for searching the max element towards the right. So the first thing that comes to mind is just to write a simple for loop with var `i` is starting from zero and i is less the `arr.length`.

Then let's print out every element first:-
```
const replaceElements = function(arr) {
    for(let i=0;i<arr.length;i++){
       console.log("element at index",i,arr[i]);
    }  
};
```

Now when you are trying to replace element 17(first element) with the greatest element. Obviously, I have to iterate over the rest of the elements and find the maximum element from the rest of the subarray. So what we can do easily is we can write another function, which will return the greatest element from the rest of the subarray.

```
const replaceElements = function(arr) {
    function greatestElement(startIndex) {
        let tempGreatestElement = arr[startIndex];
        for(let j=startIndex+1; j< arr.length;j++){
            if(tempGreatestElement < arr[j]) {
                tempGreatestElement = arr[j];
            }
        }
        return tempGreatestElement;
    }
    for(let i=0;i<arr.length;i++){
        // console.log("element at index",i,arr[i]);
        const greatestElementFromSubArray = greatestElement(i+1);
    }
};
```
So in this case, we can pass the starting index from which we need to search for the function. For example, when we are at index zero we need to search from index 1 to the right end. So, this function can take an input parameter as the start index. And after that, we can then try to search on the rest of the elements for the greatest element. By calling `greatestElement` function will actually be returning the largest element from the subarray. 
In this function, first, we have to initialise the first element as the greatest element and then we search for the rest of the elements, if there is an element greater than the current greatest element, we assign that as the greatest element.

For example, when we are reading for the first time. We'll first assign a temporary greatest element as `18` and then we will iterate over the rest of the elements. And if we find any greatest element other than 18 in the entire iteration, we will replace 18 with that greater element. And towards the end of our loop or the iteration, we will have the greatest element from the subarray.

Turns out, we might have to do some modifications in the main for loop. What will happen if I run into the last element is, the `i + 1` value will be not be defined. Because when I am on the last index `i`, `i+1` will not be a valid element value to be passed as start index to `greatestElement` function.

So let's keep this for loop till the second last element and let's run the code again:-

```
const replaceElements = function(arr) {
    function greatestElement(startIndex) {
        let tempGreatestElement = arr[startIndex];
        for(let j=startIndex+1; j< arr.length;j++){
            if(tempGreatestElement < arr[j]) {
                tempGreatestElement = arr[j];
            }
        }
        return tempGreatestElement;
    }
    for(let i=0;i<arr.length-1;i++){ // index changed here
        // console.log("element at index",i,arr[i]);
        const greatestElementFromSubArray = greatestElement(i+1);
        arr[i] = greatestElementFromSubArray; // replace the current element with greatest element
    }   
};
```
We have also replaced the element at the current index with the greatest element in the above code.
Final task for us is to replace the last element with -1 and return the array from the function:-

```
const replaceElements = function(arr) {
    function greatestElement(startIndex) {
        let tempGreatestElement = arr[startIndex];
        for(let j=startIndex+1; j< arr.length;j++){
            if(tempGreatestElement < arr[j]) {
                tempGreatestElement = arr[j];
            }
        }
        return tempGreatestElement;
    }
    for(let i=0;i<arr.length-1;i++){
        // console.log("element at index",i,arr[i]);
        const greatestElementFromSubArray = greatestElement(i+1);
        arr[i] = greatestElementFromSubArray;
    }
    arr[arr.length-1] = -1;  // replace last element
    // console.log("array after replacements",arr);
    return arr;    // return array from function
};
```

Now let's try to run our code on all the test cases and see if it is working properly. If there is an issue we will know as well. Our submission is accepted. So, this is a valid submission.

This is simply how I have solved the problem and there might be better solutions to this. Currently, this is what I came up with. If you have any better solutions, feel free to tell them in the comments section and I will probably share that with others as well. That's it from my end, I hope you understood this problem.

You can also refer to video-based explanation on Youtube for learning this in much more detail:-

%[https://youtu.be/9F0g3aB-_hU]

We will cover more such competitive programming problems in the upcoming articles in this series. 

I create content about Web Application tutorials and general programming. If this is something that interests you, please share the article with your friends and connections. You can also subscribe to my newsletter to get updates every time I write something!

Thank you for reading, If you have reached so far, please like the article, It will encourage me to write more such articles. Do share your valuable suggestions, I appreciate your honest feedback!

I would love to connect with you on [Twitter](https://twitter.com/saurabhnative) | [Instagram](https://www.instagram.com/coder_who_dreams/).

You should definitely check out my other Blogs:

- [Popular frontend interview questions](https://coderwhodreams.hashnode.dev/popular-frontend-interview-questions-and-answers-part-1)

- [Solving LeetCode array problems using Javascript - Part 1](https://coderwhodreams.hashnode.dev/solving-leetcode-array-problems-using-javascript-part-1)

- [Learn how to build Christmas greeting using CSS Animations](https://coderwhodreams.hashnode.dev/learn-how-to-build-christmas-greeting-using-css-animations)

See you in my next article, Take care!!