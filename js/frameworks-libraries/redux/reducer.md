#### Reducers

- Reducers can be made up of many reducers.
  - Makes a copy of state. Applies changes to that. Then all slices are combined into new state.
    - The copies are passed to the root reducer, who pastes copies together.
- Takes an an action and a next state.
