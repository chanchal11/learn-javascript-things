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
