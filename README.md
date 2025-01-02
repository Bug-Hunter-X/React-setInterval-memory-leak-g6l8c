# React setInterval memory leak
This repository demonstrates a common mistake in React applications: using `setInterval` inside a `useEffect` hook without properly cleaning it up. This leads to memory leaks and potential performance issues.

## Bug
The `bug.js` file contains a React component that increments a counter every second using `setInterval`.  The issue is that the `setInterval` function is never stored in a variable and thus cannot be cleared when the component unmounts or when the dependency array changes.  This leads to the interval continuing to run, consuming resources even after the component is no longer needed.

## Solution
The `bugSolution.js` file provides the corrected code.  The key change is storing the interval ID returned by `setInterval` in a variable (`intervalId`).  The `useEffect` hook's cleanup function then uses `clearInterval(intervalId)` to stop the interval when the component unmounts or when the dependency array changes.