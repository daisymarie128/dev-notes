## Stateless Functions

```

const Item = props => <div>This is my item.</div>;
  ```

- Have no lifecycle methods
  - Rendered every time a state change occurs higher up the component tree.
- No this. No refs.

The advantage of writing this way opposed to using classes, are that this forces you to separate any logic and data handling from the UI, which avoids any state handling inside representation components.

#### Things to avoid
Avoid defining a function inside the function component as a new function will be created every time the functional component is called.

***Dont do***
```

const Item = ({...}) => {
  const handleSomething = e => path(['event', 'target'], e)
  return (
    // ...
  )
}
```

***To avoid that***

Pass the function as a prop or define it outside the component.

```
const handleSomething = e => path(['event', 'target'], e)
const Item = props => <div>This is my item.</div>;
```
