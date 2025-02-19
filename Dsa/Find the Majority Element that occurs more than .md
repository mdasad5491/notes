function hasPairWithSum(arr, target) {
    let numMap = new Map();
    
    for (let num of arr) {
        let complement = target - num;
        if (numMap.has(complement)) {
            return true; // Pair found
        }
        numMap.set(num, true);
    }
    
    return false; // No pair found
}

// Example usage:
console.log(hasPairWithSum([1, 4, 7, 12], 16)); // true (4 + 12)
console.log(hasPairWithSum([2, 3, 5, 8], 10)); // false
