# Shorthand attributes
It's not uncommon to have an attribute where the name and value are the same, like src={src}.
```
<script>
	let src = 'tutorial/image.gif';
	let alt = 'ginger man'
</script>

<img {src} {alt}>
```

Svelte automatically updates the DOM when your component's state changes.