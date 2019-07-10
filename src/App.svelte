<script>
	import Intro from './components/Intro.svelte';
	import Nav from './components/Nav.svelte';
	import Main from './components/Main.svelte';
	import Footer from './components/Footer.svelte';

	import { onMount } from 'svelte';

	let intro = false;
	let showApp = true;

	const stateChangeDuration = 800;
	const appStates = {
		ABOUT: 0,
		PROJECTS: 1,
		BLOG: 2,
		CONTRIB: 3,
		CONTACT: 4
	}

	let currentState = appStates.ABOUT;

	// onMount(() => {
	// 	intro = true;
	// })

	const loadApp = () => {
		intro = false;
		setTimeout(() => {
			showApp=true;
		}, 1000);
		//showApp = true;
	}

	const changeState = (state) => {
		if (state === currentState) return;
        // console.log(state);
        switch (state) {
            case 0:
                currentState = appStates.ABOUT;
                break;
            case 1:
                currentState = appStates.PROJECTS;
                break;
            case 2:
                currentState = appStates.BLOG;
                break;
            case 3:
                currentState = appStates.CONTRIB;
                break;
            case 4:
                currentState = appStates.CONTACT;
				break;
			default:
				currentState = appStates.ABOUT;
				break;
        }
    }
</script>

<style>
	.app {
		position: absolute;
		display: flex;
		flex-flow: column nowrap;
		align-items: center;
		background-color: var(--main-background-color);
		width: 100%;
		height: 100vh;
		overflow: hidden;
		z-index: 1;
	}
	.app:after {
        background:var(--secondary-background-color);
        bottom: 0;
        content: '';
        display: block;
        height: 20%;
        left: 0;
        position: absolute;
        right: 0;
        transform: skewY(-4.8deg);
        transform-origin: 100%;
        z-index: -1;
    }
	img {
        margin-bottom: 1em;
        /* position: sticky; */
        /* top: 0; */
        z-index: 0;
    }
</style>

<main class="app">
	{#if intro}
		<Intro loadApp={loadApp} />
	{/if}
	{#if showApp}
		<Nav changeState={changeState} currentState={currentState} appStates={appStates} />
		<Main stateChangeDuration={stateChangeDuration} currentState={currentState} appStates={appStates} />
		<Footer />
	{/if}
</main>
