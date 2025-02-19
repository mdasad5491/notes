# Two Sum Problem Solutions

## Brute Force Solution and Optimise solution 


```javascript


var twoSum = function (arr, target) {
    for (var i = 0; i < arr.length; i++) {
        for (var j = 0; j < arr.length; j++) {
            if (arr[i] + arr[j] == target && i != j) {
                return [i, j];
            }
        }
    }
};




function twoSum(nums, target) {
    let map = new Map(); 
    
    for (let i = 0; i < nums.length; i++) {
        let complement = target - nums[i]; 
        if (map.has(complement)) {
          console.log("hello",map.get(complement))
            return [map.get(complement), i]; 
        }

        map.set(nums[i], i); 
    }

    return [];
}
