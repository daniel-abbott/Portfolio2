<script>
    export let title;
    export let id;
</script>

<style>
    .textblock {
        background-color: white;
        width: 95%;
        margin-bottom: 1em;
        border-radius: 0.3em;
        z-index: 1;
    }
    .textblock-text {
        padding-left: 0.5em;
    }
</style>

<section id={id} class="textblock">
    <div class="textblock-text">
        <h1>{title}</h1>
        <p>Words</p>
    </div>
</section>