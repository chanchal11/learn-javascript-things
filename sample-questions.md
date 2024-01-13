## flat an array
```
const ARR = [1, [[[2], [3, [4, [5, [6, [7]]]]]]]]

function flatUtils(arr, out){
   
   for(let i=0;i < arr.length;i++){
    //   console.log({ ai: arr[i], out});
        if(Array.isArray(arr[i])){
            flatUtils(arr[i], out);
        }else {
            out.push(arr[i]);
        }
   } 
}

function flat(arr){
    const out = [];
    flatUtils(arr, out);
    return out;
}

console.log(flat(ARR));
```
## output of following
```
console.log([1,2,3] + [4,5,6]); // 1,2,34,5,6
```

## output of following
```
(function () {
    try {
     throw new Error("");
    }catch(e){
       console.log(a);
       var a = 1, b = 2;	
    }
    console.log(a);
    console.log(b); 	 	
})();
/*
   undefined
   1
   2
*/
```
## example of how you can use setInterval in react functional components
```
import { React, useState, useEffect } from "react";
import { useMemo } from "react/cjs/react.production.min";
import "./styles.css";

export default function App() {
  const [counter, setCounter] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCounter(counter + 1);
    }, 1000);
    console.log("second");

    return () => {
      clearInterval(interval);
      console.log("first");
    };
  });

  return <h1>{counter}</h1>;
}

```

## Example of Deboucing
```
import { useCallback, useEffect, useRef, useState } from "react";

const INTERVAL = 500;
const debounce = (fn, delay) => {
  let timerId;
  return (...args) => {
    clearTimeout(timerId);
    timerId = setTimeout(() => fn(...args), delay);
  };
};
export default function App() {
  const [text, setText] = useState("");
  const [dText, setDtext] = useState("");

  const debouceHandler = useCallback((data) => setDtext(data), [text]);

  return (
    <div className="App">
      <input
        onChange={(e) => {
          setText(e.target.value);
          debouceHandler(e.target.value);
        }}
      />
      <p>{dText}</p>
    </div>
  );
}

```
