# Pure Component

This component is similar to React.Component. The difference between them is that `React.PureComponent` implements `shouldComponentUpdate`, with a shallow prop and state comparison.

## Usage

If your component renders the same result given the same props and state, you can use `React.PureComponent` for a performance boost.

## Code example

In the example we have three components, the `Jobs` component is the container, and there are other two, `JobsOnHold` and `JobsRunning`, which are the children of the container.

`Jobs` has a state called `job` which is set to the same value every two seconds and is passed as a prop to its children.

`JobsOnHold` is a `React.Component` and `JobsRunning` is a `React.PureComponent`.

All the components are logging a message on its `render()` method. Notice that the message `JOBS RUNNING ::: RENDERED` appears only once on your console, because the prop passed to this component never change, therefore the component never gets re-rendered again.

When a parent component gets re-rendered, all the children get re-rendered as well, unless you set `shouldComponentUpdate` to return `false`.

[Example](./index.html)

## Takeaways

- A pure component implements `shouldComponentUpdate` with a shallow props and state comparison.
- If a parent component be a `PureComponent` none of its children will re-render, in case there are no updates on state and props of the parent component.

Reference: [React.PureComponent](https://reactjs.org/docs/react-api.html#reactpurecomponent)
