# useEffect

## What are Events
Nested functions inside components that do things rather than just calculate them. Event handlers contain “side effects” (they change the program’s state) caused by a specific user action (for example, a button click or typing).

## What are effects?
Effects let you specify side effects that are caused by rendering itself, rather than by a particular event.

## When do effects run?
At the commit stage (render (create the component) vs commit(add component to DOM))
[see react lifecycle](https://react.dev/learn/render-and-commit)

## Syntax
`useEffect(setup, dependencies?)`
### params:
* setup: function with logic, can include a 'cleanup' function that runs before each time the effect re-runs with updated dependencies, and finally before the component unmounts
* dependencies: The list of all reactive values referenced inside of the setup code. Reactive values include props, state, and all the variables and functions declared directly inside your component body
> [!NOTE]
> If you pass no dependency array at all (as opposed to an empty array), the Effect runs after every single render (and re-render) of the component.
### returns:
`undefined`

## #### Removing unnecessary dependencies
https://react.dev/learn/removing-effect-dependencies#removing-unnecessary-dependencies

## Caveats
https://react.dev/reference/react/useEffect#caveats

## When to use useEffect?
* To connect with external systems (external servers, browser DOM, non-react libraries etc.)
* To fetch data
* To control a non-react widget

## Useful reading
https://maxrozen.com/race-conditions-fetching-data-react-with-useeffect
