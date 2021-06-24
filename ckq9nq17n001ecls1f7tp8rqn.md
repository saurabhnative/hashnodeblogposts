## Leetcode Array Problem Solutions-part 4 (remove Duplicates From Sorted Array)

In today's article, we are going to solve another leetcode problem and the statement for today's problem is to remove duplicate from a sorted array.
Link to the problem:-
https://leetcode.com/explore/learn/card/fun-with-arrays/511/in-place-operations/3258/

Agenda:-
- We are going to remove duplicate elements from a sorted array using javascript. 
- We will also learn how to use the splice method to remove elements from an array.

We are given an integer array which is called nums with elements sorted in non-decreasing order, that is the elements will be in ascending order. We need to remove the duplicates, but they should be inplace that is we cannot clone the array or create another array for removing the duplicates, we need to do it in the same array itself.
The order of the elements should also be kept as it is after removing duplicates. We are supposed to return the length of the array after removing duplicate elements.

Let's build a solution to the problem step by step:-

Since we need to remove duplicates from this array obviously we need to iterate it over once, so we can either use for loop or map function to iterate over the input array:-

```
const removeDuplicates = function(nums) {
    nums.map((element, index) => {
        console.log("element", element);
        console.log("index", index);
   });
}
```
Within every iteration or cycle of this loop, we need to check whether duplicates exist.  We can see if the next element is a duplicate by using if condition as shown below:-

```
        ...
        console.log("index", index);
        if(element === nums[index+1]) {
            // code to remove duplicate elements
        }
```

We need to declare a variable to keep a track of duplicate elements. If a duplicate element exists then we will increment the value of this variable. To calculate the total number of duplicate elements we will run a for loop from the next element of the current index to the length of the array as shown below:-

```
       ...
       if(element === nums[index+1]) {
            let numberOfDuplicates = 0;
            for(let i=index+1;i<nums.length;i++) {
                if(nums[i] === element) {
                    ++numberOfDuplicates;
                } else {
                    break;
                }
            }
            console.log("numberOfDuplicates", numberOfDuplicates);
        }
``` 

We have added a break statement in the else block so that we can stop iteration once the total number of duplicate elements are calculated.
Next, we need to remove the duplicate elements from the array for which are going to use the array  [splice](https://www.w3schools.com/jsref/jsref_splice.asp) method. In the case of splice, the first input is generally the index from which we need to remove or add the indices and the second input is the total number of elements we need to remove. 

In our case, we need to remove the elements from next index of current elements and the total elements to be removed are total number of duplicate elements stored in the `numberOfDuplicates` variable above.

So the final solution to the problem is as shown below:-

```
const removeDuplicates = function(nums) {
    nums.map((element, index) => {
        console.log("element", element);
        console.log("index", index);
        if(element === nums[index+1]) {
            let numberOfDuplicates = 0;
            for(let i=index+1;i<nums.length;i++) {
                if(nums[i] === element) {
                    ++numberOfDuplicates;
                } else {
                    break;
                }
            }
            // console.log("numberOfDuplicates", numberOfDuplicates);
            nums.splice(index+1, numberOfDuplicates);
        }
    });
    // console.log("output array", nums);
    return nums.length;
};
```

We return the length of the array in the end since it is asked in the problem statement. If we run this solution on leetcode it is accepted for all the test cases. We have commented `console.log` statements in the final solution since they are no longer required.

After we've finished any kind of computer programming problem, we usually go for time complexity calculation. We have a map function at the top which can be considered as a for loop and there is an inner for loop for calculation duplicate elements. So with nested for loops like this time complexity for the solution would be O(n<sup>2</sup>).

Now, there might be some better solutions that might reduce the time complexity but I have covered the simplest possible solution that I could think of. As we learn more data structures and algorithms in future, we will try to come up with better solutions.

If you found this tutorial useful, hit the like button, follow my blog, and if there is anyone you know who will benefit from such articles in data structures in JavaScript or preparing for interviews, please share it with them as well. Goodbye and have a nice day.

---------------------------------------------------------------------------------------------------

Join my discord server for help :  
🌐 discord server: https://discord.gg/AWbhSUWWaX

---------------------------------------------------------------------------------------------------

Suggestions and Feedback
  
🐦 TWITTER:  https://twitter.com/saurabhnative

🎥 INSTAGRAM:  https://www.instagram.com/saurabhnative/?hl=en

---------------------------------------------------------------------------------------------------

For collaboration, connect with me on Twitter

🐦 TWITTER: https://twitter.com/saurabhnative

---------------------------------------------------------------------------------------------------

Support me on Kofi

🤝 https://ko-fi.com/saurabhmhatre

---------------------------------------------------------------------------------------------------

