## check if it is a prime number
```
function isPrime(num){
    for(let i=2; i<= num/2 ;i++ ){
        if(num % i == 0){
            return false;
        }
    }
    return true;
}
```

## get max & 2nd max prime numbers from given array
```
// a = 73, 1, 6, 8, 98, 2, 1

function getMaxAndSecondMax(array){
    
    let max = -Infinity;
    let secondMax = -Infinity;
    
    for(let i=0; i< array.length; i++ ){
            const isPrimeNum = isPrime(array[i]);
            if( isPrimeNum && array[i] > max){
                max = array[i];
            }else if( isPrimeNum && array[i] > secondMax ){
                secondMax = array[i];
            }
    }
    
    return { max, secondMax };
}

console.log( getMaxAndSecondMax([73, 1, 6, 8, 98, 2, 1]) )
```

## Create a function that compares two strings if they are anagrams of each other
```
function getFreq(str){
    const map = {};
    for(let i=0; i < str.length; i++ ){
        if(map.hasOwnProperty(str[i])){
            map[str[i]]++;
        }else {
            map[str[i]] = 1;
        }
    }
    return map;
}

function isFreqsSame(freq1, freq2){
    const keys = Object.keys(freq1);
    for(let i=0; i< keys.length ; i++ ){
        if(freq1[keys[i]] != freq2[keys[i]] ){
            return false;
        }
    }
    return true;
}

function checkAnagram(str1, str2){
    const freq1 = getFreq(str1);
    const freq2 = getFreq(str2);
    return isFreqsSame(freq1, freq2);
}

console.log(checkAnagram("car", "arc"));

```

## from a array that can have a number or an another array - give maximum values of each array
```
// input [1,[4,6,[8,3]],[11,12],2]
// output [2,6,12,8] or [2,12,6,8]
// [n, a[n,n,a], a[n,n], n]

//[4,6,[8,3]] => [6, 8]

function getMaxs(arr){
    let outArr = [];
    let max = null;
    let arrToProcess = [];
    for(let i=0; i< arr.length; i++){
        if(!Array.isArray(arr[i])) {
            if(max && arr[i] > max ){
                max = arr[i];
            }else if(max == null) {
                max = arr[i];
            }
        }
        else {
            arrToProcess.push(arr[i]);                
        }
    }
    outArr.push(max);
    
    for(let i=0; i< arrToProcess.length;i++){
            outArr.push(...getMaxs(arrToProcess[i]));   
    }
    
    return outArr;
}

console.log(getMaxs([1,[4,6,[8,3]],[11,12],2]));
```

##Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

Example 1:

Input: intervals = [[1,3],[2,6],[8,19],[15,18]]

Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

Output: [[1,6],[8,10],[15,18]]

Example 2:

Input: intervals = [[1,4],[4,5]]
Intervals [1,4] and [4,5] are considered overlapping.
Output: [[1,5]]


Constraints:

    1 <= intervals.length <= 10^4
    intervals[i].length == 2
    0 <= starti <= endi <= 10^4


```
var merge = function(intervals) {
    	intervals.sort( (a,b) => a[0] -  b[0] );
        let i = 1;
        while(i < intervals.length){
            const first = intervals[i-1];
            const second = intervals[i];
            if(first[1] > second[1] ){
                intervals.splice(i,1);
            }else if(first[1] >= second[0] && first[1] <= second[1] ){
                intervals.splice(i,0, [first[0], second[1]]);
                intervals.splice(i+1,1);
                intervals.splice(i-1,1);
            }
            i++;
        }
        return intervals;
};

console.log(merge([[1,4],[4,5],[8,10],[15,18]]));
```

## Sorted squared values of given sorted array

- Test Case 1 Input [-4,-1,0,3,10] => [ 0, 1, 9, 16, 100 ]
- Test Case 2 Input [-4,-3,-1] => [ 1, 9, 16 ]

```
function getSqrs(nums){
    let l = 0, r = nums.length - 1;
    while(l < r){
        if(nums[l] >= 0){
            break;
        }
        
        const leftHandValue = -1 * nums[l];
        const RightHandValue = nums[r];
        if( leftHandValue >= RightHandValue ){
            nums.splice(r+1, 0, nums[l]);
            nums.splice(0, 1);
        }
        r--;
    }
    return nums.map((v) => v * v );
}

console.log(getSqrs( [-5, -3, -2]));
```

## Sort the array from mid element in opposite direction

- Given -> [5,6,2, 7, 8, 7, 31]
- Output => [2, 5,6, 7, 31, 8, 7]

```
// using bubble sort
function customSort(arr){
    let middleIndex = Math.floor((arr.length - 2 ) / 2);
    for(let i = 0; i<middleIndex; i++ ){
        for(let j=i+1; j <=middleIndex; j++ ){
            if(arr[i]> arr[j]){
                let temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }    
        }    
    }        
    for(let i = middleIndex+ (arr.length % 2 == 0 ? 1 : 2); i< arr.length - 1; i++ ){
        for(let j=i+1; j <= arr.length; j++ ){
            if(arr[i] < arr[j]){
                let temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }    
        }
    }
    return arr;
}

console.log(customSort([5,6,2, 7, 8, 7, 31]));
```
