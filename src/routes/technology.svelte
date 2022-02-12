<script>
import Pageheading from "$lib/Pageheading.svelte";
import { technology } from "../data.json";
import { onMount } from 'svelte';

let currIndex = 0;
let imgOrientation;
onMount(
    ()=>{
        const mediaObj = window.matchMedia("(min-width: 55rem)");
        const handler = (ev) => {
            imgOrientation = ev.matches ? "portrait" : "landscape";
        }

        handler(mediaObj);

        mediaObj.addEventListener("change", handler);
    }
)

</script>

<svelte:head>
    <title>Space Tourism | Technology</title>
</svelte:head>

<div class="background"></div>
<div class="grid-container">
    <Pageheading marker="03" heading="Space launch 101" />
    <main>
        <div class="image-wrapper">
            <img src="{technology[currIndex].images[imgOrientation]}" alt="{technology[currIndex].name}">
        </div>
    
        <div class="switcher">
            {#each technology as tech, i}
            <div class="switch" class:active="{currIndex === i}" on:click={()=>{currIndex=i}}>{i+1}</div>
            {/each}
        </div>
    
        <article>
            <h2>
                <span class="subheading2">The terminology...</span>
                <em class="heading3">{technology[currIndex].name}</em>
            </h2>
            <p class="description">
                {technology[currIndex].description}
            </p>
        </article>
    </main>
</div>

<style>
    .background {
        position: fixed;
        z-index: -100;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-size: cover;
        background-image: url('/assets/technology/background-technology-mobile.jpg');
    }
    .grid-container {
        width: 100%;
        height: 100%;
        display: grid;
        grid-template-rows: auto 1fr;
        grid-auto-flow: row;
        align-items: stretch;
        justify-items: stretch;
    }
    main {
        display: flex;
        flex-flow: column nowrap;
        gap: 2rem;
        justify-content: space-between;
        align-items: center;
        text-align: center;

        margin: 2rem 0;
    }
    .image-wrapper {
        width: 100vw;
        height: 45vw;
        max-width: 100vmin;
        height: 45vmin;
    }
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .switcher {
        display: flex;
        flex-flow: row wrap;
        gap: 1rem;
    }
    .switch {
        width: 2.5rem;
        height: 2.5rem;
        font: 1rem/2.5rem var(--bellefair);

        color: var(--white);
        border-radius: 50%;
        border: 1px solid rgba(255, 255, 255, 0.25);
        text-align: center;
        cursor: pointer;
    }
    .switch:hover {
        border-color: rgba(255, 255, 255, 1)
    }
    .switch.active {
        background-color: var(--white);
        color: var(--black);
    }

    article{
        padding: 0 var(--gutter);
    }
    article span {
        font-size: 0.875rem;
    }
    em {
        display: block;
        line-height: 1.5;
    }
    .description {
        margin-top: 1rem;
        max-width: 28.625rem;
        min-height: 11em;
    }

    @media (min-width: 33rem) {
        .background {
            background-image: url('/assets/technology/background-technology-tablet.jpg');
        }
        main {
            gap: 2.5rem;
        }
        .switch {
            width: 3.75rem;
            height: 3.75rem;
            line-height: 3.75rem;
            font-size: 1.5rem;
        }
        article span {
            font-size: 1rem;
        }
    }
    @media (min-width: 55rem) {
        .background {
            background-image: url('/assets/technology/background-technology-desktop.jpg');
        }
        main {
            flex-flow: row nowrap;
            margin-left: var(--gutter);
            margin-bottom: 4rem;
            text-align: left;
        }
        .switcher {
            order: 1;
            flex: 0 0 5rem;
        }
        .switch {
            width: 5rem;
            height: 5rem;
            line-height: 5rem;
            font-size: 2rem;
        }
        article {
            order: 2;
            padding: 0;
        }
        .description {
            max-width: 27.75rem;
        }
        .image-wrapper {
            order: 3;
            align-self: flex-start;

            width: auto;
            height: auto;
            max-width: 40%;
            max-height: 30rem;
        }
    }
</style>