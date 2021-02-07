# Updating Arrays and Objects
Because Svelte's reactivity is triggered by assignments, using array methods like push and splice won't automatically cause updates. For example, clicking the button doesn't do anything.

One way to fix that is to add an assignment that would otherwise be redundant:
```
function addNumber() {
	numbers.push(numbers.length + 1);
	numbers = numbers;
}
```
But there's a more idiomatic solution:
```
function addNumber() {
	numbers = [...numbers, numbers.length + 1];
}
```