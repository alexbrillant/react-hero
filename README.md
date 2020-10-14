# react-awesome


## Testing

[react-testing](https://testing-library.com/docs/react-testing-library/intro)

Why ? 

- Test behavior of components instead of implementation
- Easily test with nodes using `data-testid`
- Encourages best practices

# Hooks 

[hooks](https://reactjs.org/docs/hooks-intro.html)

Why ? 

- Use state and hook in the components lifecycle
- Replaces render prop pattern 
- Colocate related logic
- Share reusable behaviors independent of component implementations


## Forms 

[react-hook-form](https://react-hook-form.com/)

Why ? 

- Compact Code
- Isolates Component Re-renders
- Input change subscriptions
- Faster mounting

```javascript
import React from "react";
import { useForm } from "react-hook-form";

const Example = () => {
  const { handleSubmit, register, errors } = useForm();
  const onSubmit = values => console.log(values);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        name="email"
        ref={register({
          required: "Required",
          pattern: {
            value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
            message: "invalid email address"
          }
        })}
      />
      {errors.email && errors.email.message}

      <input
        name="username"
        ref={register({
          validate: value => value !== "admin" || "Nice try!"
        })}
      />
      {errors.username && errors.username.message}

      <button type="submit">Submit</button>
    </form>
  );
};
```

## State container

[react-redux](https://react-redux.js.org/api/hooks) with hooks

Why ? 


- Subscribe to the Redux store and dispatch actions, without having to wrap your components in connect()

```javascript
import React, { useCallback } from 'react'
import { useDispatch } from 'react-redux'

export const CounterComponent = ({ value }) => {
  const dispatch = useDispatch()
  const incrementCounter = useCallback(
    () => dispatch({ type: 'increment-counter' }),
    [dispatch]
  )

  return (
    <div>
      <span>{value}</span>
      <MyIncrementButton onIncrement={incrementCounter} />
    </div>
  )
}

export const MyIncrementButton = React.memo(({ onIncrement }) => (
  <button onClick={onIncrement}>Increment counter</button>
))
```

