# Async/Await
Most web applications have to deal with asynchronous data at some point. Svelte makes it easy to await the value of  directly in your markup:
```
{#await promise}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
```
Only the most recent promise is considered, meaning you don't need to worry about race conditions.

