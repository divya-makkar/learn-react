# useEffect
A hook that lets you synchronize a component with external systems

## Types of logic in a component
### Render code
Logic used to return JSX (markup) based on props and state.
> [!IMPORTANT]
> Render logic should be a pure function. I shouldn't update the state, only generate an output based on the given inputs (props/state).
### Events
Nested functions inside components that do things rather than just calculate them. Event handlers contain “side effects” (they change the program’s state) caused by a specific user action (for example, a button click or typing).
### Effects
Effects are similar to events, except that they let you specify side effects that are caused by rendering itself, rather than by a particular event.
> [!NOTE]
> Effects are what the `useEffect` hook is used for!

## When do effects run?
At the commit stage (when a component is added to DOM). [see react lifecycle](https://react.dev/learn/render-and-commit)

## useEffect Syntax
`useEffect(setup, dependencies?)`
### params:
* setup: function with logic, can include a 'cleanup' function that runs before each time the effect re-runs with updated dependencies, and finally before the component unmounts
* dependencies: The list of all reactive values referenced inside of the setup code. Reactive values include props, state, and all the variables and functions declared directly inside your component body
> [!NOTE]
> If you pass no dependency array at all (as opposed to an empty array), the Effect runs after every single render (and re-render) of the component.
### returns:
`undefined`

## When to use useEffect?
* To connect with external systems (external servers, browser DOM, non-react libraries etc.)
* To fetch data
> [!IMPORTANT]
> When fetching data inside a useEffect, always use a cleanup function to avoid race conditions (see useful reading links for more details) 
* To control a non-react widget

## When not to use useEffect
* To transform data for rendering
* To handle user events
* To make expensive calculations, slow api calls etc. (in these cases `useMemo` should be used)
* To update state based on props
* To reset all state when a component prop changes
* To synchronize state variables in different components

## Useful reading
1. [useEffect caveats](https://react.dev/reference/react/useEffect#caveats)
2. [Fixing Race Conditions in React with useEffect](https://maxrozen.com/race-conditions-fetching-data-react-with-useeffect)
3. [You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect)
4. [Removing unnecessary dependencies](https://react.dev/learn/removing-effect-dependencies#removing-unnecessary-dependencies)
