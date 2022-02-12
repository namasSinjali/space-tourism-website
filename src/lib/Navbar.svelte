<script>
    import { page } from '$app/stores';
    const navItems = [
        ["Home", "/"],
        ["Destination", "/destination"],
        ["Crew", "/crew"],
        ["Technology", "/technology"],
    ]
    let hidden = true;
</script>

<div class="topnav">
    <div>
        <img class="logo" src="./assets/shared/logo.svg" alt="logo">
    </div>

    <nav class:hidden>
        <ol>
            {#each navItems as [name, path], counter}
            <li><a href="{path}" class:active="{$page.url.pathname === path}">
                <span class="counter">0{counter}</span>
                <span class="name">{name}</span>
            </a></li>
            {/each}
        </ol>
    </nav>

    <button class="nav-toggle" on:click={()=>{hidden=!hidden}}>
        {#if hidden}
        <img src="./assets/shared/icon-hamburger.svg" alt="Open navigation">
        {:else}
        <img src="./assets/shared/icon-close.svg" alt="Close navigation">
        {/if}
    </button>
</div>                    

<style>
    .topnav{
        width: 100%;
        height: 6rem;

        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        padding: 0 min(3.5rem, var(--gutter));
    }
    .logo{
        height: 2.5rem;
    }
    nav {
        position: fixed;
        top: 0;
        right: 0;
        z-index: 5;

        padding-top: 7rem;
        height: 100vh;
        width: clamp(7rem, 67.73vw, 16rem);
        
        background: rgba(255, 255, 255, 0.04);
        backdrop-filter: blur(35px);

        transform: translateX(0);
        transition: all 250ms ease-out;
    }
    nav.hidden {
        transform: translateX(100%);
    }
    ol{
        text-transform: uppercase;
        font-size: 1rem;
        font-family: var(--barlow-condensed);
        color: var(--white);
        letter-spacing: 0.16875rem;

        margin-left: 2rem;

        list-style: none;

        display: flex;
        flex-flow: column nowrap;
        gap: 1.25rem;
    }
    a {
        display: block;
        height: 1.875rem;
        line-height: 1.875;
        border-width: 0 4px 0 0;
        border-style: solid;
        border-color: transparent;
    }
    a:hover {
        border-color: rgba(255, 255, 255, 0.5);
    }
    a.active {
        border-color: rgba(255, 255, 255, 1);
    }
    .counter {
        font-weight: bold;
        margin-right: 0.6875rem;
    }
    .nav-toggle {
        position: relative;
        z-index: 6;
        background: unset;
        border: none;
        outline: none;
    }

    @media (min-width: 33rem) {
        .nav-toggle {
            display: none;
        }
        .topnav {
            padding-right: 0;
        }
        nav{
            align-self: stretch;
            position: static;

            padding: 0 var(--gutter);
            height: auto;
            width: auto;

            transform: unset;
        }
        nav.hidden {
            transform: unset;
        }

        ol{
            height: 100%;
            align-items: stretch;

            font-size: 0.875rem;
            letter-spacing: 0.1475rem;

            margin-left: unset;

            flex-flow: row nowrap;
            align-items: center;
            gap: 2.31rem;
        }
        li {
            height: 100%;
        }

        a {
            border-width: 0 0 3px 0;
            height: 100%;
            display: flex;
            align-items: center;
        }
        .counter {
            display: none;
        }
    }
    @media (min-width: 55rem) {
        .counter {
            display: block;
        }
        .topnav {
            margin-top: 2rem;
        }
        .logo {
            order: 1;
        }
        .topnav::before {
            content: "";
            border-top: #fff 1px solid;
            opacity: 0.25;

            order: 2;
            flex: 1 0 0;
            z-index: 1;

            margin-right: -2rem;
            margin-left: calc(var(--gutter) - 6rem);
        }
        nav {
            order: 3;
        }
        ol {
            justify-content: center;
            gap: 3rem;
            font-size: 1rem;
            letter-spacing: 0.16875rem;
        }
    }
</style>