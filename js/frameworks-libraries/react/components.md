## 🚀 React Components

React Components should be split into either containers or presentational components.

### Containers

- Concerned with how things work.
- May contain both presentational and container components.
  - But usually don't have any DOM markup of their own except for some wrapping divs
  - Usually never have styles.
- Provide data and behaviour to presentational or other container components.
- Call Redux actions and provide these as callbacks to presentational components.
- Tend to serve as data sources.
- Usually generated using higher order components such as connect().

### Presentational

- Concerned with how things look.
- May contain both presentational and container components
- Usually have DOM markup and styles of their own.
- Have no dependencies on the rest of the app, such as Redux actions or stores.
- Doesn't specify how data id loaded or mutated.
- Receive data and callbacks via props.
- Rarely have their own state (usually UI state rather than data).
- Should try to be written as functional components, unless they need state, lifecycle hooks or performance optimizations.


By using this approach it's easier to separate logic concerns with your app, while also making your app easier to understand. Plus it makes presentational component easier to be reused.
