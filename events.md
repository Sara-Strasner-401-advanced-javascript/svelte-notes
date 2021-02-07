# Events
As we've briefly seen already, you can listen to any event on an element with the on: directive:
```
<div on:mousemove={handleMousemove}>
	The mouse position is {m.x} x {m.y}
</div>
```

You can also declare event handlers inline:
```
<div on:mousemove="{e => m = { x: e.clientX, y: e.clientY }}">
	The mouse position is {m.x} x {m.y}
</div>
```
The quote marks are optional, but they're helpful for syntax highlighting in some environments.

## Event Modifiers
DOM event handlers can have modifiers that alter their behaviour. For example, a handler with a once modifier will only run a single time:
```
<script>
	function handleClick() {
		alert('no more alerts')
	}
</script>

<button on:click|once={handleClick}>
	Click me
</button>
```
The full list of modifiers:
1. preventDefault - calls event.preventDefault() before running the handler. Useful for client-side form handling, for example.
1. stopPropagation - calls event.stopPropagation(), preventing the event reaching the next element
1. passive - improves scrolling performance on touch/wheel events (Svelte will add it automatically where it's safe to do so)
1. nonpassive - explicitly set passive: false
1. capture - fires the handler during the capture phase instead of the bubbling phase ()
1. once - remove the handler after the first time it runs
1. self - only trigger handler if event.target is the element itself
You can chain modifiers together, e.g. on:click|once|capture={...}.

## Bubbling/Event Forwarding
Unlike DOM events, component events don't bubble. If you want to listen to an event on some deeply nested component, the intermediate components must forward the event.

In this case, there's an Outer.svelte component that contains <Inner/>.

Svelte gives us a handy shorthand - an `on:message` event directive without a value means 'forward all message events.'
```
<script>
	import Inner from './Inner.svelte';
</script>
```

Event forwarding works for DOM events too.
```
<button on:click>
	Click me
</button>
````