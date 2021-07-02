# form-hook

A react hook for form validation

# Installation

`npm i @mitish13/form-hook --save`

## Provided validation types:

1. First it gives chance to user to put the value in field and let the field loose its focus
2. Then it will validate after every keystroke, to provide instant validation

## How to use

Hook will take two things as an argument

1. Field validatation logic : pass a function to tell how to validate a value
2. Default value : pass a value, It will be set as a initial value of state ( default is set to '')

Here is one simple form validation example

```
import { useForm } from "@mitish13/form-hook";

const Form = () => {
  const {
    value, // value of field
    valueChangeHandler, // field onChange handler
    hasError, // Use this to show error if any
    isValueValid, // use this to validate value against predicate function given
    inputBlurHandler, // use this to validate on every key stroke after field looses its focus (onBlur handler)
    resetForm, // use this to reset form field to empty
  } = useForm((value) => value !== "", "");

  const submitHandler = (e) => {
    e.preventDefault();
    if (isValueValid) console.log("Text will be submitted if it is valid");
  };

  const resetHandler = () => {
    resetForm();
  };

  return (
    <form onSubmit={submitHandler}>
      <label>Add Text</label>
      <input
        type="text"
        value={value}
        onBlur={inputBlurHandler}
        onChange={valueChangeHandler}
      ></input>
      <br />
      {hasError && <p style={{ color: "red" }}>Text can't be empty</p>}
      <button type="submit">submit</button>
      <button onClick={resetHandler}>Reset</button>
    </form>
  );
};

export default Form;
```

## Sandbox Link of above example
https://codesandbox.io/s/form-hookexample-qkl62
