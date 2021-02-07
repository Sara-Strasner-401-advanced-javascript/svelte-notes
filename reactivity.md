# Reactivity/Statements
Svelte automatically updates the DOM when your component's state changes. Often, some parts of a component's state need to be computed from other parts (such as a fullname derived from a firstname and a lastname), and recomputed whenever they change.

For these, we have reactive declarations. They look like this:
```
let count = 0;
$: doubled = count * 2;
```
