<script>
    export let width;
    export let image;
    export let title;
    export let description;
</script>

<style>
    div {
        width: var(--width);
    }
</style>

<div style="--width: {width}">
    <p>{image}</p>
    <p>{title}</p>
    <p>{description}</p>
</div>
