> Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution.

`给定一个整数数组，返回两个数的索引，使它们相加为一个特定的目标。你可以假设每个输入都有一个解。`

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

- 解法1：

```
var twoSum = function (nums, target) {
    var len = nums.length;
    for (var i = 0; i < len - 1; i++) {
        for (var j = i + 1; j < len; j++) {
            if (nums[i] + nums[j] == target) {
                return [i, j];
            }
        }
    }
    return null;
};

console.log(twoSum([2, 7, 11, 15], 9));
```
```
### 举一反三
var twoSum = function (nums, target) {
    var len = nums.length;
    var arr = [];
    for (var i = 0; i < len - 1; i++) {
        for (var j = i + 1; j < len; j++) {
            if (nums[i] + nums[j] == target) {
                arr.push([i,j])
            }
        }
    }
    return arr;
    return null;
};

console.log(twoSum([1,2,3,4,5,6,7,8,9], 10));
// [[0,8][1,7][2,6][3,5]]

```


- 解法2：

```
var twoSum = function(nums, target) {
    var temp = [];
    for (var i = 0; i < nums.length; i++) {
        if (temp[target - nums[i]] !== undefined) {
            return [temp[target - nums[i]], i];
        }
        if (!temp[nums[i]]) {
            temp[nums[i]] = i;
        }
    }
};
```
> nums=[1,3,5,7,9,11] , target=10

|i|nums[i]|target-nums[i]|temp[target-nums[i]]|
| :---: | :---: | :---: | :---: |
| 0 | 1 | 10-1 ,9 | tmmp[9] |
| 1 | 3 | 10-3 ,7 | tmmp[7] |
| 2 | 5 | 10-5 ,5 | tmmp[5] |
| 3 | 7 | 10-7 ,3 | tmmp[3] |
| 4 | 9 | 10-9 ,1 | tmmp[1] |

