## Write Recursive Function that takes following input and gives following out
```
const inObj = {
    a: {
      b: {
        d: 1
      }
    },
    e: {
      g: 8
    }
  }
  /*o/p: a.b.c = 1, a.d.c=1 ,d.g = 8 */
  
  function recursivePrint(obj, output, parent){
    Object.keys(obj).forEach((key) => {
      if(typeof obj[key] == 'object'){
        if(parent){
          recursivePrint(obj[key], output, parent+'.'+key);
        }else {
          recursivePrint(obj[key], output, key);
        }
      }else {
        if(parent){
          output[parent+'.'+key] = obj[key];
        }else {
          output[key] = obj[key];
        }
      }
    });
  } 
  
  function sol( obj ) {
  	const output = {}; 
  	recursivePrint(obj, output);
  	console.log(output); 
  }
  
  sol(inObj)
```

## Find out the ranges
```
// Find out the ranges 
	   const inputArray = [ 1, 2, 3, 4, 5, 6, 9, 13, 14, 15, 16, 17 ];
// 	   output = [1-6, 9, 13-17, 20];

function findRanges(arr){
    const output = [];
    let start = arr[0];
    let end = arr[0];
    for(let i=1; i < arr.length; i++){
        if(arr[i] == arr[i-1] + 1 ){
            end = arr[i];
        }else {
            if(start == end){
                output.push(start);
            }else {
                output.push(`${start}-${end}`);
            }
            start = arr[i];
            end = arr[i];
        }
    }
    
    if(start == end){
        output.push(start);
    }else {
        output.push(`${start}-${end}`);
    }
    
    return output;
}

console.log(findRanges(inputArray));
```

## Check if its mountain - first strictly increasing then strictly descresing
```
const input = [0,3,2,1];

function isMountain(arr){
    let increaseFlag = true;
    let flagSwitched = false;
    
    if(arr.length < 3){
        return false;
    }
    
    if(arr.length > 2 && arr[0] > arr[1]){
        return false;
    }
    
    for(let i=1; i< arr.length; i++){
        if(increaseFlag && !flagSwitched && arr[i] > arr[i-1]){
            continue;
        }else if(increaseFlag && !flagSwitched && arr[i] < arr[i-1]  ){
            increaseFlag = false;
            flagSwitched = true;
        }else if(!increaseFlag && flagSwitched &&  arr[i] < arr[i-1] ){
            continue;
        }else {
            return false;
        }
    }
    return flagSwitched;
}

console.log(isMountain([0, 3, 5, 4, 1]));

// [

//   { array: [1, 2], result: false },

//   { array: [3, 3, 3], result: false },

//   { array: [1, 2, 2, 1], result: false },

//   { array: [2, 2, 1], result: false },

//   { array: [1, 2, 3, 4], result: false },

//   { array: [5, 4, 3, 2, 1], result: false },

//   { array: [1, 2, 3, 4, 5], result: false },

//   { array: [0, 2, 3, 2, 3, 2, 1], result: false },

//   { array: [1, 3, 2, 4, 1], result: false },

//   { array: [0, 1, 0], result: true },

//   { array: [-3, -2, -1, -2, -3], result: true },

//   { array: [-1, -2, -3], result: false },

//   { array: [0, 3, 5, 4, 1], result: true }

// ]
 
```
