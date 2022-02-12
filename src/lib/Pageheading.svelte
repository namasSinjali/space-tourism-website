<script>
    export let marker, heading;
</script>

<h1 class="heading5">
    <span class="marker">
        {marker}
    </span>
    <span>
        {heading}
    </span>
</h1>

<style>
    h1 {
        color: var(--white);
        padding: 0 var(--gutter);
        text-align: center;
    }
    .marker {
        opacity: 0.25;
        margin-right: 1em;
    }
    @media (min-width: 33rem) {
        h1 {
            margin-top: 2rem;
            text-align: left;
        }
    }
</style>