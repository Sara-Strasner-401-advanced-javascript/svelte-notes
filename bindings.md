# Bindings
As a general rule, data flow in Svelte is top down - a parent component can set props on a child component, and a component can set attributes on an element, but not the other way around.

Sometimes it's useful to break that rule. Take the case of the `<input>` element in this component - we could add an on:input event handler that sets the value of name to event.target.value, but it's a bit... boilerplatey. 

Instead, we can use the `bind:value` directive: `<input bind:value={name}>`


```
<script>
	let name = 'world';
</script>

<input bind:value={name}>

<h1>Hello {name}!</h1>
```
This means that not only will changes to the value of name update the input value, but changes to the input value will update name.

## Binding Checkbox Inputs
Checkboxes are used for toggling between states. Instead of binding to input.value, we bind to input.checked:
```
<input type=checkbox bind:checked={yes}>
```

## Binding Group Inputs
If you have multiple inputs relating to the same value, you can use `bind:group` along with the `value` attribute. Radio inputs in the same group are mutually exclusive; checkbox inputs in the same group form an array of selected values.