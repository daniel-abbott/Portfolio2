<script>
	import Nav from './components/Nav.svelte';
	import Main from './components/Main.svelte';
</script>

<style>
	.app {
		display: flex;
		flex-flow: column nowrap;
		align-items: center;
	}
</style>

<div class="app">
	<Nav />
	<Main />
</div>
