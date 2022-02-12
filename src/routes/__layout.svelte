<script>
    import Navbar from "$lib/Navbar.svelte"

    import "../app.css";
</script>

<Navbar />

<div>
    <slot></slot>
</div>

<style>
    :global(#svelte) {
        min-height: 100vh;
        display: grid;
        grid-template-rows: auto 1fr;
    }
    div{
        position: relative;
    }
</style>