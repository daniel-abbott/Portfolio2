<script>
    import { fade, scale } from 'svelte/transition';
    import { quintOut } from 'svelte/easing';

    export let modalData;
    export let closeModal;
</script>

<style>
    @keyframes mouseOver {
        from {
            color: var(--nav-text-color);
        }
        to {
            color: var(--nav-highlight-color);
        }
    }
    @keyframes mouseLeave {
        from {
            color: var(--nav-highlight-color);
        }
        to {
            color: var(--nav-text-color);
        }
    }
    .modal-background {
        height: 100%;
        width: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        position: absolute;
        z-index: 90;
        pointer-events: none;
    }
    .modal {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        width: 90%;
        height: 80%;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 100;
        background-color: var(--secondary-body-color);
        color: var(--secondary-text-color);
        border-radius: var(--standard-radius);
        overflow: hidden;
        pointer-events: all;
    }
    .modal-title {
        width: 100%;
        background-color: blue;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0.5em;
    }
    .modal-close {
        cursor: pointer;
        animation-name: mouseLeave;
        animation-duration: 0.2s;
        padding-right: 0.5em;
    }
    .modal-close:hover {
        animation-name: mouseOver;
        animation-duration: 0.2s;
        color: var(--nav-highlight-color);
    }
    .modal-text {
        display: flex;
        flex-flow: row wrap;
        /* padding-left: 1em; */
        /* padding-right: 1em; */
        /* background-color: red; */
        overflow: auto;
        width: 100%;
        height: 100%;
    }
    h2 {
        margin: 0;
        padding-left: 0.5em;
    }
    p {
        padding-left: 1em;
        padding-right: 1em;
    }
</style>

<div transition:fade="{{ duration: 400 }}" class="modal-background">
    <div class="modal" transition:scale="{{ duration: 800, easing: quintOut }}">
        <div class="modal-title">
            <h2>{modalData.title}</h2>
            <span class="modal-close" on:click={closeModal}>Close</span>
        </div>
        <div class="modal-text">
            <p>{@html modalData.fullDescription}</p>
        </div>
    </div>
</div>