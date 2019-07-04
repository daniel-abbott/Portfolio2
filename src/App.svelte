<script>
	import Nav from './components/Nav.svelte';
	import Main from './components/Main.svelte';
	import Footer from './components/Footer.svelte';
</script>

<style>
	.app {
		display: flex;
		flex-flow: column nowrap;
		align-items: center;
		background-color: whitesmoke;
		height: 100%;
	}
	img {
        margin-bottom: 1em;
        /* position: sticky; */
        /* top: 0; */
        z-index: 0;
    }
</style>

<main class="app">
	<Nav />
	<img src="content/testpic.png" width="100%" height="400px" />
	<Main />
	<Footer />
</main>
