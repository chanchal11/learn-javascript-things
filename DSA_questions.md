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
