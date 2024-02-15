# useMemo
By default, when a component re-renders, all the code inside the component is re-run, and all the children in the component are re-rendered. If we want to avoid this behaviour for some functions (expensive calculations) or components we can use the `useMemo` hook. `useMemo` lets us cache the result of a calculation between re-renders
The process of caching results from a calculation is called `memoization`, which is where the name of this hook id derived from.

## useMemo syntax
`useMemo(calculateValue, dependencies)`
### params:
* calculateValue: The function calculating the value that you want to cache
[!NOTE]
> Should be a pure function, should take no arguments, and should return a value of any type
* dependencies: The list of all reactive values referenced inside of the calculateValue code 
### returns:
* On first render: The result of calling `calculateValue` with no arguments
* On next re-renders: an already stored value from the last render (if the dependencies haven’t changed), or call `calculateValue` again, and return the result that `calculateValue` has returned
### example:
```
import { useMemo } from 'react';

function TodoList({ todos, tab }) {
  const visibleTodos = useMemo(
    () => filterTodos(todos, tab), // <-- calculateValue function
    [todos, tab] // <-- dependencies array
  );
  // ...
}
```

## When to use useMemo?
* To skip expensive recalculations
* To skip re-rendering of components
* To memoize a dependency of another Hook
[!NOTE]
> To check whether we need to add useMemo or not, we have certain tools like React profiler, or performance web APIs to measure component performance

## Before deciding to use useMemo:


## Useful reading
1. [React Profiler](https://legacy.reactjs.org/blog/2018/09/10/introducing-the-react-profiler.html)
2. [Performance APIs](https://developer.mozilla.org/en-US/docs/Web/API/Performance_API)
