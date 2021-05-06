## Solving LeetCode array problems using Javascript Part 1

Hello, curious stranger on the internet, in today's post, we will solve a LeetCode array problem using Javascript. We are interested in solving is `Merge Sorted Array` problem from LeetCode mentioned below:-
https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3253/

In this problem, we are supposed to merge two arrays nums1 and nums2 into one sorted array.

The number of elements initialized in nums1 and nums2 is m and n respectively. We may assume that nums1 has a size equal to m + n such that it has enough space to hold additional elements from nums2.

Let's understand this problem with an example:-

Example 1:

We have two input arrays: 
```
nums1 = [1,2,3,0,0,0], m = 3, 
nums2 = [2,5,6], n = 3
```
m is the actual elements of interest in nums1 and n is the total number of elements in nums2
 
Here `nums1` array has 3 prefilled elements and the next 3 zeroes are to be replaced by elements by elements in the `nums2` array. 
Also, the resultant array should be sorted as shown below:-
```
Output: [1,2,2,3,5,6]
```

One approach for solving this problem is to transfer all the elements from the second array in place on zeroes in the first array and then sort the values as shown below:-

![Screenshot 2021-05-05 at 11.34.37 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1620237889774/roWxbgR2-.png)

We are going to make use of the `startIndex` variable in our solution to point to the index of the first zero in the `num1` array. This will be used to transfer elements one by one from the second to the first array.

We can now start writing our code by first initializing the `startIndex` value:-
```
const merge = function(nums1, m, nums2, n) {
    // startIndex in the index of first element to be replaced in the array
    const startIndex = nums1.length - n;
};
```
It is calculated by subtracting the total number of elements in the second from the length of the first array.
Then we apply a for loop to transfer elements from the second array to their desired places in the first array:-
```
const merge = function(nums1, m, nums2, n) {
    const startIndex = nums1.length - n;
    for(let i=startIndex;i < nums1.length;i++) {
        nums1[i] = nums2[i-startIndex];
    }
};
```
The for loop starts from the `startIndex` value since this is from where element replacement should start. It runs till the length of the first array.
The replacement strategy is to pick up an element from the second array using the `i-startIndex` value and place it in the first array at index `i`.
Once we are done with replacements of elements, we can sort the elements using the sort method in Javascript:-
```
const merge = function(nums1, m, nums2, n) {
    const startIndex = nums1.length - n;
    for(let i=startIndex;i < nums1.length;i++) {
        nums1[i] = nums2[i-startIndex];
    }
    nums1.sort(function(a,b){return a-b});
};
```
The sort function by default run string matching, so we have defined a custom function to sort it on numeric values. More details about this can be found here:-
https://www.w3schools.com/js/js_array_sort.asp

That finishes out the entire logic for solving this problem. You can find the solution explained in much more detail in video format here:-

%[https://youtu.be/up5vvOnJPUY]

If you liked this article kindly upvote it and become a sponsor for motivating me to write more such articles in future.
