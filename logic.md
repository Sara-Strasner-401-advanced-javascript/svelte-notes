# Logic
HTML doesn't have a way of expressing logic, like conditionals and loops. Svelte does.

To conditionally render some markup, we wrap it in an if block:
```
{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{:else}
	<button on:click={toggle}>
		Log in
	</button>
{/if}
```

- A `#` character always indicates a block opening tag. 
- A `/` character always indicates a block closing tag. 
- A `:` character, as in `{:else}`, indicates a block continuation tag.

## Logic/Each Blocks
If you need to loop over lists of data, use an each block:

```
<ul>
	{#each cats as cat}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a></li>
	{/each}
</ul>
```

The expression (cats, in this case) can be any array or array-like object (i.e. it has a length property). You can loop over generic iterables with each `[...iterable]`.

You can get the current index as a second argument, like so:
```
{#each cats as cat, i}
	<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
		{i + 1}: {cat.name}
	</a></li>
{/each}
```

If you prefer, you can use destructuring - `each cats as { id, name }` - and replace `cat.id` and `cat.name` with id and name.

Be sure to specify a unique identifier for the each block:
```
{#each things as thing (thing.id)}
	<Thing current={thing.color}/>
{/each}
```