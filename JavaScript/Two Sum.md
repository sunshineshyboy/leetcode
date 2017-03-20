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

|i|nums[i]| temp[nums[i]] | temp[nums[i]] = i | target-nums[i] | temp[target-nums[i]] | # |
| :---: |  :---:  | :---: | :---: | :---: | :---: | :---: |
| 0 | 1 | temp[1] | temp[1]=0 | 10-1 ,9 | tmmp[9] | tmmp[9] == undefined |
| 1 | 3 | temp[3] | temp[3]=1 | 10-3 ,7 | tmmp[7] | tmmp[7] == undefined |
| 2 | 5 | temp[5] | temp[5]=2 | 10-5 ,5 | tmmp[5] | tmmp[5] == undefined |
| 3 | 7 | temp[7] | temp[7]=3 | 10-7 ,3 | tmmp[3] | 此时temp[3]等于1，执行并return |
| 4 | 9 | temp[9] | temp[9]=4 | 10-9 ,1 | tmmp[1] | |

> nums=[8,3,25,47,69,11,55,71,91] , target=82

|i|nums[i]| temp[nums[i]] | temp[nums[i]] = i | target-nums[i] | temp[target-nums[i]] | # |
| :---: |  :---:  | :---: | :---: | :---: | :---: | :---: |
| 0 | 8 | temp[8] | temp[8]=0 | 82-8 ,74 | tmmp[74] | tmmp[74] == undefined |
| 1 | 3 | temp[3] | temp[3]=1 | 82-3 ,79 | tmmp[79] | tmmp[79] == undefined |
| 2 | 25 | temp[25] | temp[25]=2 | 82-25 ,57 | tmmp[57] | tmmp[57] == undefined |
| 3 | 47 | temp[47] | temp[47]=3 | 82-47 ,35 | tmmp[35] | tmmp[35] == undefined |
| 4 | 69 | temp[69] | temp[69]=4 | 82-69 ,13 | tmmp[13] | tmmp[13] == undefined |
| 5 | 11 | temp[11] | temp[11]=4 | 82-11 ,71 | tmmp[71] | tmmp[71] == undefined |
| 6 | 55 | temp[55] | temp[55]=4 | 82-55 ,27 | tmmp[27] | tmmp[27] == undefined |
| 7 | 71 | temp[71] | temp[71]=4 | 82-71 ,11 | tmmp[11] | tmmp[11] == 此时undefined等于4，执行并return |

