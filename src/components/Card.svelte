<script>
    export let width;
    export let image;
    export let title;
    export let description;
</script>

<style>
    @keyframes upscale {
        from {transform: scale(1);}
        to {transform: scale(1.05);}
    }
    @keyframes downscale {
        from {transform: scale(1.05);}
        to {transform: scale(1);}
    }
    .card {
        animation-name: downscale;
        animation-duration: 0.2s;
        background-color: white;
        width: var(--width);
        margin: 0.5em;
        border: 1px solid gray;
        border-radius: 0.3em;
        /* box-shadow: 0 1px 5px 2px rgba(0, 0, 0, 0.1); */
    }
    .card:hover {
        animation-name: upscale;
        animation-duration: 0.2s;
        transform: scale(1.05);
    }
    
    .card-text {
        padding-left: 0.2em;
        padding-right: 0.2em;
    }
    img {
        border-top-left-radius: 0.3em;
        border-top-right-radius: 0.3em;
    }
</style>

<div class= "card" style="--width: {width}">
    {#if image}
        <img src={image} alt="placeholder" width="100%" />
    {/if}
    <div class="card-text">
        <h3>{title}</h3>
        <p>{description}</p>
    </div>
</div>
