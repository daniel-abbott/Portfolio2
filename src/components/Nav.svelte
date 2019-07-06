<script>
    import { fly } from 'svelte/transition';
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
    h3 {
        padding-left: 2em;
    }
    div {
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        background-color: white;
        width: 100%;
        box-shadow: 0 3px 5px 2px rgba(0, 0, 0, 0.2);
        z-index: 100;
    }
    ul {
        display: flex;
        padding-right: 2em;
    }
    a {
        animation-name: mouseLeave;
        animation-duration: 0.2s;
        margin-left: 1em;
        color: black;
        text-decoration: none;
    }
    a:hover {
        animation-name: mouseOver;
        animation-duration: 0.2s;
        color: orange;
    }
    a:active {
        color: orangered;
    }
</style>

<div in:fly="{{y: -100, duration: 1000}}">
    <h3>Daniel Abbott</h3>
    <ul>
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#blog">Blog</a>
        <a href="#contrib">Contributions</a>
        <a href="#contact">Contact</a>
    </ul>
</div>
