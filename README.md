# Task

You've learned about some advanced React APIs, React.cloneElement and React.Children.map that allow you to modify the children of a component dynamically. In this exercise, you'll use these APIs to build a RadioGroup component.

On HTML, an input of type radio offers a checked property to determine whether a radio button is selected or not.

When building a radio group in React, in other words, a component that represents a set of choices where only one can be selected at a time, an initial implementation might look like this:

<RadioOption checked={false} onChange={handleOnChange} value="1" />
<RadioOption checked={true} onChange={handleOnChange} value="2" />
<RadioOption checked={false} onChange={handleOnChange} value="3" />
However, this approach is not ideal because it requires the user of the component to keep track of the state of each radio button, as well as setting state change handlers for each option.

Wouldn't it be great to remove any redundancies and reduce the state to the bare minimum while still keeping the functionality intact? Well, this is a great example where component composition shines and enables developers to use a more intuitive and simpler set of props to define a component's API.

Instead of having the user of the component to keep track of the state of each radio button, you can have a parent RadioGroup component that is aware of the current selection and provides a handler to manage any selection change, without you having to explicitly pass the checked and onChange props to each RadioOption component.

The RadioGroup component can then leverage the children prop and use both React.cloneElement and React.Children.map to internally pass the checked and onChange props to each RadioOption child.

<RadioGroup selected={selectedValue} onChange={handleOnChange}>
  <RadioOption value="1" />
  <RadioOption value="2" />
  <RadioOption value="3" />
</RadioGroup>