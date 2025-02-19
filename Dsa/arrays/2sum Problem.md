Profile
Blogs

DSA Sheets
System Design

Striver's DSA Playlist

SDE Core Sheets
Striver's CP Sheet

Saved Notes

CW Fullstack Final

User
Two Sum : Check if a pair with given sum exists in Array


656

25
Problem Statement: Given an array of integers arr[] and an integer target.

1st variant: Return YES if there exist two numbers such that their sum is equal to the target. Otherwise, return NO.

2nd variant: Return indices of the two numbers such that their sum is equal to the target. Otherwise, we will return {-1, -1}.

Note: You are not allowed to use the same element twice. Example: If the target is equal to 6 and num[1] = 3, then nums[1] + nums[1] = target is not a solution.

Examples:

Example 1:
Input Format: N = 5, arr[] = {2,6,5,8,11}, target = 14
Result: YES (for 1st variant)
       [1, 3] (for 2nd variant)
Explanation: arr[1] + arr[3] = 14. So, the answer is “YES” for the first variant and [1, 3] for 2nd variant.

Example 2:
Input Format: N = 5, arr[] = {2,6,5,8,11}, target = 15
Result: NO (for 1st variant)
	[-1, -1] (for 2nd variant)
Explanation: There exist no such two numbers whose sum is equal to the target.
Disclaimer: Don't jump directly to the solution, try it out yourself first.

Problem Link.

Naive Approach(Brute-force approach): 

Intuition: For each element of the given array, we will try to search for another element such that its sum is equal to the target. If such two numbers exist, we will return the indices or “YES” accordingly.

Approach:

First, we will use a loop(say i) to select the indices of the array one by one.
For every index i, we will traverse through the remaining array using another loop(say j) to find the other number such that the sum is equal to the target (i.e. arr[i] + arr[j] = target).
Observation: In every iteration, if the inner loop starts from index 0, we will be checking the same pair of numbers multiple times. For example, in iteration 1, for i = 0, we will check for the pair arr[0] and arr[1]. Again in iteration 2, for i = 1, we will check arr[1] and arr[0]. So, to eliminate these same pairs, we will start the inner loop from i+1.

Dry Run: Given array, nums = [2,1,3,4], target = 4

Using the naive approach, we first select one number and then find the second one.

For index 0, element= 2,
Then, we iterate through indices 1 to 3 to check if target – x, i.e. 4 – 2 = 2 exists. 2 does not exist from index 1 to 3, we move to the next index.

For index 1, element=1,
Then, we iterate through indices 2 to 3 to find if target – x, i.e. 4 – 1 = 3 exists. 3 exists at index 2, so we store the indices 1 and 2, break the loop, and return the indices.

Code Variant 1:

C++
Java
Code Variant 2:

C++
Java
Better Approach(using Hashing): 

Intuition: Basically, in the previous approach we selected one element and then searched for the other one using a loop. Here instead of using a loop, we will use the HashMap to check if the other element i.e. target-(selected element) exists. Thus we can trim down the time complexity of the problem.

And for the second variant, we will store the element along will its index in the HashMap. Thus we can easily retrieve the index of the other element i.e. target-(selected element) without iterating the array.

Approach:

The steps are as follows:

We will select the element of the array one by one using a loop(say i).
Then we will check if the other required element(i.e. target-arr[i]) exists in the hashMap.
If that element exists, then we will return “YES” for the first variant or we will return the current index i.e. i, and the index of the element found using map i.e. mp[target-arr[i]].
If that element does not exist, then we will just store the current element in the hashMap along with its index. Because in the future, the current element might be a part of our answer.
Finally, if we are out of the loop, that means there is no such pair whose sum is equal to the target. In this case, we will return either “NO” or {-1, -1} as per the variant of the question.
Dry Run: Given array, nums = [2,3,1,4], target = 4

Note: Here x denotes the currently selected element.

For index 0, x = 2, and currently map is empty.
We try to find if target – x = 4 – 2 = 2 is present in the map or not.
For now, 2 does not exist on the map.
And we store the index of element 2. i.e., mp[2] = 0,

For index 1, x = 3
We try to find if target – x = 4  – 3 = 1 is present in the map or not.
For now, 1 does not exist on the map.
And we store the index of element 3. i.e., mp[3] = 1,

For index 2, x = 1 
We try to find if target – i = 4  – 1 = 3 is present in the map or not. 3 exists in the map, so we store index 2 and the value stored for key 3 in the map and break the loop. And return [1,2].
Code for Variant 1:

C++
Java
Code for Variant 2:

C++
Java
Optimized Approach(using two-pointer): 

Intuition: In this approach, we will first sort the array and will try to choose the numbers in a greedy way.

We will keep a left pointer at the first index and a right pointer at the last index. Now until left < right, we will check the sum of arr[left] and arr[right]. Now if the sum < target, we need bigger numbers and so we will increment the left pointer. But if sum > target, we need to consider lesser numbers and so we will decrement the right pointer. 

If sum == target we will return either “YES” or the indices as per the question.
But if the left crosses the right pointer, we will return “NO” or {-1, -1}.

Approach:

The steps are the following:

We will sort the given array first.
Now, we will take two pointers i.e. left, which points to the first index, and right, which points to the last index.
Now using a loop we will check the sum of arr[left] and arr[right] until left < right.
If arr[left] + arr[right] > sum, we will decrement the right pointer.
If arr[left] + arr[right] < sum, we will increment the left pointer.
If arr[left] + arr[right] == sum, we will return the result.
Finally, if no results are found we will return “No” or {-1, -1}.
Dry Run: Given array, nums = [2,1,3,4], target = 4

First, we sort the array. So nums after sorting are [1,2,3,4]

We take two-pointers, left and right. The left points to index 0 and the right points to index 3.

Now we check if nums[left] + nums[right] == target. In this case, they don’t sum up, and nums[left] + nums[right] > target so that we will reduce right by 1.

Now, left = 0, right=2

Here, nums[left] + nums[right] == 1 + 3 == 4, which is the required target, so we will return the result.

Code:

C++
Java
Special thanks to Pranendu Bikash Pradhan and Sudip Ghosh and KRITIDIPTA GHOSH for contributing to this article on takeUforward. If you also wish to share your knowledge with the takeUforward fam, please check out this article.


