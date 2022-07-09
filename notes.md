# Course Notes

Every time react senses a change, it re-renders

## JSX

- JSX elements are made using calls to React.createElement()
- Void tags (e.g. `<Component/>`)
- Valid JSX may sometimes be invalid html

## Components

- when using an html `class` attribute, we use `className` (e.g. `<div className="">`)

## Hooks

- `useState` depends heavily on the order that it's called. So don't have conditional hooks or inside of loops.
- `useEffect` is like a function that we can wrap around something that will do stateful things that are going to live outside of the component
- Dependency array in `useEffect` - whenever the given variable(s) change, the hook will be called. Pass empty array if we want it to run once in the beginning. If no dependency is given, the hook will be called whenever any state variable changes.

### Custom Hooks

- prefixing custom hook names with `use` is intentional

## Handling User Input

- When using a submit listener (i.e. onSubmit), first put `e.preventDefault()`
- There are lots of ways to submit a form, but just listen for submit events
- synthetic events are React events, not actual DOM events

## Component Composition
- Expressions will work inside curly braces, whereas statements won't

## Building for production
- React in production will be much smaller size than development. Read https://btholt.github.io/complete-intro-to-react-v7/lessons/core-react-concepts/react-dev-tools

## Strict mode
- Makes sure that the React app will be futureproof and compatible when newer versions get released.
- Shipping strict mode in production has no effect.