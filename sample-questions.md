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
import React, { useState } from "react";

const DebounceExample = () => {
  const [inputText, setInputText] = useState("");
  const [debouncedText, setDebouncedText] = useState("");

  const debounce = (fn, delay) => {
    let timerId;
    return (...args) => {
      clearTimeout(timerId);
      timerId = setTimeout(() => fn(...args), delay);
    };
  };

  // Debounced version of setText
  const debouncedSetText = debounce((text) => setDebouncedText(text), 1500);

  const handleInputChange = (e) => {
    setInputText(e.target.value);
    debouncedSetText(e.target.value);
  };

  return (
    <div>
      <h2>Debounce Example</h2>
      <input
        type="text"
        placeholder="Type something..."
        value={inputText}
        onChange={handleInputChange}
      />
      <p>Debounced Text: {debouncedText}</p>
    </div>
  );
};

export default DebounceExample;
```

## sum(1)(2)(3)()
```
function sum(a){
  return function(b){
    if(b){
      return sum(a+b);
    }else {
      return a;
    }
  }
}

console.log(sum(1)(2)(3)()); // Output: 6
```

## difference between a function and react hook-
```
a function is a general programming concept, while a React hook is a specific type of function
introduced in React for managing state and side effects in functional components.

Functions can be used for a wide range of purposes, while React hooks are specific to React components and their lifecycle.
```

## How to combine two selectors in redux ?
In Redux, you can use the reselect library to create selectors and combine them efficiently. Reselect provides a createSelector function that allows you to create memoized selectors, which will only recalculate their result if their input selectors have changed.

Here's an example of combining multiple selectors using reselect:

Install reselect:
```npm install reselect``` and
Create selectors for individual pieces of state:
```
// selectors.js

import { createSelector } from 'reselect';

const getUsers = (state) => state.users;
const getFilter = (state) => state.filter;

export const getFilteredUsers = createSelector(
  [getUsers, getFilter],
  (users, filter) => {
    // Your logic to filter users based on the filter
    return users.filter((user) => user.name.includes(filter));
  }
);
```
In this example, getFilteredUsers is a selector that depends on getUsers and getFilter. It applies some filtering logic to the users based on the filter value.

Use the combined selector in your component:
```
// YourComponent.js

import React from 'react';
import { connect } from 'react-redux';
import { getFilteredUsers } from './selectors';

const YourComponent = ({ filteredUsers }) => {
  // Use filteredUsers in your component
  return (
    <div>
      {filteredUsers.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}
    </div>
  );
};

const mapStateToProps = (state) => {
  return {
    filteredUsers: getFilteredUsers(state),
  };
};

export default connect(mapStateToProps)(YourComponent);
```
Now, filteredUsers in your component will be automatically updated whenever the users or filter state changes, thanks to the memoization provided by reselect.
