<script>
import Pageheading from "$lib/Pageheading.svelte";
import { crew } from "../data.json";

let currIndex = 0;
</script>

<svelte:head>
    <title>Space Tourism | Crew</title>
</svelte:head>
<div class="background"></div>
<Pageheading marker="02" heading="Meet your crew" />
<main>
    <picture>
        <source srcset="{crew[currIndex].images.webp}" />
        <img src="{crew[currIndex].images.png}" alt="{crew[currIndex].name}">
    </picture>

    <div class="switcher">
        {#each crew as member, i}
        <div class="dot" class:active="{currIndex === i}" on:click={()=>{currIndex = i}}></div>
        {/each}
    </div>

    <article>
        <h2>
            <b class="heading4">{crew[currIndex].role}</b>
            <em class="heading3">{crew[currIndex].name}</em>
        </h2>
        <p class="bio">{crew[currIndex].bio}</p>
    </article>
</main>

<style>
    .background {
        position: fixed;
        z-index: -100;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-size: cover;
        background-image: url('/assets/crew/background-crew-mobile.jpg')
    }
    main {
        display: grid;
        grid-template-columns: auto;
        grid-auto-rows: auto;
        grid-template-areas: "picture" "switcher";
        padding: 0 var(--gutter);
        margin-top: 2rem;
        justify-items: center;
        text-align: center;
        gap: 2rem;
    }
    picture {
        grid-area: picture;
        height: 60vmin;
        border-bottom: solid 1px #3b3b3b;
        justify-self: stretch;
    }
    picture img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }

    .switcher {
        grid-area: switcher;
        display: flex;
        flex-flow: row nowrap;
        gap: 1rem;
    }
    .dot {
        width: 0.625rem;
        height: 0.625rem;
        border-radius: 50%;
        background-color: rgba(255, 255, 255, 0.17);
        cursor: pointer;
    }
    .dot:hover {
        background-color: rgba(255, 255, 255, 0.5);
    }
    .dot.active {
        background-color: rgba(255, 255, 255, 1);
    }

    h2 {
        margin-bottom: 1rem;
    }
    b, em {
        display: block;
        line-height: 1.5;
    }
    .bio {
        min-height: 10em;
        max-width: 27.75rem;
    }

    @media (min-width: 33rem) {
        .background {
            background-image: url('/assets/crew/background-crew-tablet.jpg');
        }
        main {
            grid-template-areas: "text" "switcher" "picture";
            margin-top: 4rem;
            margin-bottom: 0;
            padding-bottom: 0;
        }
    }
    @media (min-width: 55rem) {
        .background {
            background-image: url('/assets/crew/background-crew-desktop.jpg');
        }
        main {
            position: absolute;
            top: 0;
            margin: 0;
            grid-template-columns: 1fr 1fr;
            grid-template-rows: 5fr 1fr;
            grid-template-areas:
            "text picture"
            "switcher picture";
            justify-content: left;
            justify-items: left;
            text-align: left;
            height: 100%;
            width: 100%;
        }
        article {
            align-self: flex-end;
            margin-top: 5rem;
        }
        .switcher {
            margin-bottom: 5rem;
        }
        picture {
            height: auto;
        }
        picture img {
            object-position: bottom right;
        }
    }
</style>