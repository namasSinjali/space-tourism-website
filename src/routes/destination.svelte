<script>
    import Flexdata from '$lib/Flexdata.svelte';
    import Pageheading from '$lib/Pageheading.svelte';
    import { destinations } from '../data.json';

    let currIndex = 0;
</script>

<svelte:head>
    <title>Space Tourism | Destination</title>
</svelte:head>
<div class="background"></div>
<Pageheading marker="01" heading="Pick your destination" />
<main>
    <picture>
        <source srcset="{destinations[currIndex].images.webp}" />
        <img src="{destinations[currIndex].images.png}" alt="{destinations[currIndex].name}">
    </picture>
    
    <ul class="switcher">
        {#each destinations as destination, i}
        <li class="subheading2" class:active="{currIndex===i}" on:click={()=>{currIndex=i}}>
            {destination.name}
        </li>
        {/each}
    </ul>

    <div class="text-wrapper">
        <h2 class="heading2">
            {destinations[currIndex].name}
        </h2>
        <p>
            {destinations[currIndex].description}
        </p>
    </div>
    <Flexdata {...destinations[currIndex]} />
</main>

<style>
    .background {
        position: fixed;
        z-index: -100;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-repeat: no-repeat;
        background-size: cover;
        background-image: url('/assets/destination/background-destination-mobile.jpg')
    }
    main {
        display: grid;
        grid-template: 
            'picture' auto
            'switcher' auto
            'heading' auto
            'description' auto
            'data' auto / auto;
        justify-items: center;
        gap: 1rem;
        padding: 0 var(--gutter);
        margin-top: 1rem;
        text-align: center;
    }
    picture {
        grid-area: picture;
        align-self: center;
        height: 50vmin;
        max-height: 18.75rem;
        margin: 1rem;
    }
    picture img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }
    ul {
        grid-area: 'switcher';

        list-style: none;
        display: flex;
        flex-flow: row nowrap;
        gap: 1rem;
    }
    li {
        height: 2rem;
        border-bottom: 2px solid transparent;
        cursor: pointer;
    }
    li.active {
        border-bottom-color: var(--white);
    }
    li:hover {
        border-color: rgba(255, 255, 255, 0.5);
    }
    .text-wrapper {
        grid: 'text'
    }
    p {
        margin-bottom: 1rem;
        min-height: 10em;
    }
    @media (min-width: 33rem) {
        .background {
            background-image: url('/assets/destination/background-destination-tablet.jpg')
        }
    }
    @media (min-width: 55rem) {
        .background {
            background-image: url('/assets/destination/background-destination-desktop.jpg')
        }
        main{
            justify-items: flex-start;
            column-gap: 5rem;
            grid-template:
            'picture switcher' auto
            'picture heading' auto
            'picture description' auto
            'picture data' auto / 1fr 1fr;
            text-align: left;
            margin-top: 4rem;
        }
        picture {
            max-height: none;
            height: auto;
        }
    }
</style>