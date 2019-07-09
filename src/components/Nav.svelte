<script>
    import { fly } from 'svelte/transition';

    export let appStates;
    export let currentState;
    export let changeState;
</script>

<style>
    @keyframes mouseOver {
        from {
            color: black;
        }
        to {
            color: orange;
        }
    }
    @keyframes mouseLeave {
        from {
            color: orange;
        }
        to {
            color: black;
        }
    }
    nav {
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        background-color: white;
        width: 100%;
        box-shadow: 0 3px 5px 2px rgba(0, 0, 0, 0.1);
        z-index: 100;
    }
    h3 {
        padding-left: 2em;
    }
    ul {
        display: flex;
        padding-right: 2em;
    }
    span {
        animation-name: mouseLeave;
        animation-duration: 0.2s;
        margin-left: 1em;
        color: black;
        text-decoration: none;
        cursor: pointer;
    }
    span:hover {
        animation-name: mouseOver;
        animation-duration: 0.2s;
        color: orange;
    }
    span:active {
        color: orangered;
    }
</style>

<nav in:fly="{{y: -100, duration: 1000}}">
    <h3>Daniel Abbott</h3>
    <ul bind>
        <span on:click="{() => changeState(0)}">About</span>
        <span on:click="{() => changeState(1)}">Projects</span>
        <span on:click="{() => changeState(2)}">Blog</span>
        <span on:click="{() => changeState(3)}">Contributions</span>
        <span on:click="{() => changeState(4)}">Contact</span>
    </ul>
</nav>
