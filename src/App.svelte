<script>
	import Nav from './Nav.svelte';
	export let name;
</script>

<style>
	.app {
		display: flex;
	}
	h1 {
		color: purple;
	}
</style>

<div class="app">
	<Nav />
	<h1>Hello {name}!</h1>
</div>

