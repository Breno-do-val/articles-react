# UseState hook

It allows you to manage internal state inside a functional component.

```Javascript
  const state = useState('foo');
```

## Let's dive deeper into this function call.

When calling this useState(), you can set an initial state with any data structure and it will return the initial state
and a function to update the state.

```Javascript
  console.log(state[0]); //-> foo
```

```Javascript
  state[1]('bar');
  console.log(state[0]); //-> bar
```

But you can use array destructuring for better readability.

```Javascript
  const [state, setState] = useState('foo');
```

## Let's develop an example and write down the takeaways when using this hook.

[Example here](./useState.html)

1. As mentioned above, you can set any data structure as the initial state. On the other hand, in class components, the state is
   always an object.
   In this case, it is an empty array.

```Javascript
const [todos, setTodos] = React.useState([]);
```

2. Clicking on the button to get one more `To-do` from [JSON API](https://jsonplaceholder.typicode.com/todos/1), we override the previous
   one if we update the state as below.

```Javascript
const handleAddTodos = () => {
  fetch(`https://jsonplaceholder.typicode.com/todos/${Math.ceil(Math.random() * 10)}`)
    .then(response => response.json())
    .then(data => {
      setTodos(data);
    });
};
```

> _useState() overrides the previous state if you don't get it before changing the state, furthermore the state update is asynchronous
so you might skip a change if you don't get the previous one._

That being said, we need to change how to add more `To-do` into our array.

```Javascript
const handleAddTodos = () => {
  fetch(`https://jsonplaceholder.typicode.com/todos/${Math.ceil(Math.random() * 10)}`)
    .then(response => response.json())
    .then(data => {
      setTodos(prev => [...prev, data]);
    });
};
```

3. The `useState()` hook must be used only within functional components. This rule is valid for all the hooks.
