<script>
    export let { distance, travel } = { };
</script>

<ul>
    <li>
        <span class="subheading2">Avg. distance</span>
        <span class="subheading1">{distance}</span>
    </li>
    <li>
        <span class="subheading2">Est. travel time</span>
        <span class="subheading1">{travel}</span>
    </li>
</ul>

<style>
    ul {
        list-style: none;
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        padding: 1rem 0;
        border-top: 1px solid #3b3b4b;
        row-gap: 2rem;
        column-gap: 4rem;
        width: 100%;
    }
    li {
        display: flex;
        flex-flow: column nowrap;
        align-items: stretch;
        gap: 0.5rem;
    }
    .subheading2 {
        color: var(--light-blue);
    }
    .subheading1 {
        color: var(--white);
    }
</style>