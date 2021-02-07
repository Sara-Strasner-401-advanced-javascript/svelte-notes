# Props
So far, we've dealt exclusively with internal state - that is to say, the values are only accessible within a given component.

In any real application, you'll need to pass data from one component down to its children. To do that, we need to declare properties, generally shortened to 'props'. In Svelte, we do that with the export keyword. Edit the Nested.svelte component:
```
<script>
	export let answer;
</script>
```

We can easily specify default values for props in Nested.svelte:
```
<script>
	export let answer = 'a mystery';
</script>
```

If you have an object of properties, you can 'spread' them onto a component instead of specifying each one:
```
<Info {...pkg}/>
```