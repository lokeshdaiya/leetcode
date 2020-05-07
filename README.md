# leetcode

## 1. 1009: https://leetcode.com/problems/complement-of-base-10-integer/

Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

```
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.

```
### Answer

```
/**
 * @param {number} num
 * @return {number}
 */
var findComplement = function(num) {
    let binary = convertToBinary(num);
    return convertToDecimal(binary);
};


function convertToBinary(num) {
    let binary = '';
    while(num>0) {
        binary = `${num%2 == 1 ? 0: 1 }${binary}`;
        
        num = Math.floor(num/2);
    }
    
    
    return binary;

}

function convertToDecimal(num) {
    let sum = 0;
    for(let i = 0, j=num.length-1; i <num.length; i++, j--) {
        sum += Math.pow(2,i) * num[j]; 
    }
    
    return sum;
}

```
## 2. First Unique Character in a String

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

Examples:

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```

### Answer

```
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function(s) {
    
    let group = {};
    let i = 0;
    for(let i =0;i<s.length;i++) {
        group[s[i]]= group[s[i]] ? group[s[i]] +1 : 1; 
    }
    
   for(let i =0;i<s.length;i++) {
        if(group[s[i]] == 1) {
            return i;
        }   
    }
    
    return -1;

};

```

## 3. Majority Element

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example 1:

```
Input: [3,2,3]
Output: 3
```

Example 2:

```
Input: [2,2,1,1,1,2,2]
Output: 2
```

### Answer

/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    let group = {};
    for(let num of nums) {
        group[num] = group[num] ? group[num]+1 : 1;
    }
    
    for(let num in group) {
        if(group[num]> nums.length/2) {
            return num;
        }
    }
};
