<script>
</script>

<svelte:head>
    <title>Space Tourism</title>
</svelte:head>
<div class="background"></div>
<main>
    <header>
        <div class="hero-text">
            <div class="heading5">So, you want to travel to</div>
            <em class="heading1">Space</em>
        </div>
        <p>
            Let’s face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world experience!
        </p>
    </header>
    <section>
        <a href="./destination">
            <button>
                Explore
            </button>
        </a>
    </section>
</main>

<style>
    .background {
        position: fixed;
        z-index: -100;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-image: url('/assets/home/background-home-mobile.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: bottom;
    }
    main{
        text-align: center;

        display: flex;
        flex-flow: column nowrap;
        justify-content: space-around;
        align-items: center;
        gap: 2rem;

        padding: 0 var(--gutter);
        margin: 1rem 0;
    }
    header{
        max-width: 28.125rem;
    }
    .hero-text em {
        display: block;
        margin: 1rem 0;
    }
    button{
        background-color: var(--white);
        border: none;
        outline: none;

        width: 9.275rem;
        height: 9.275rem;
        border-radius: 50%;
        
        font-family: var(--bellefair);
        color: var(--black);
        font-size: 1.25rem;
        text-transform: uppercase;
        letter-spacing: 1.25px;
        
        transition: all 200ms ease-out;
        margin: 2rem;

        cursor: pointer;
    }
    button:hover {
        box-shadow: rgba(255, 255, 255, 0.1) 0 0 0 2rem;
    }

    @media (min-width: 33rem) {
        .background {
            background-image: url('/assets/home/background-home-tablet.jpg');
        }
        main {
            margin-top: 5rem;
        }
        button {
            width: 15rem;
            height: 15rem;
            font-size: 2rem;
            margin: 3rem;
        }
        button:hover {
            box-shadow: rgba(255, 255, 255, 0.1) 0 0 0 3rem;
        }
    }
    @media (min-width: 55rem) {
        .background {
            background-image: url('/assets/home/background-home-desktop.jpg');
            background-position: right;
        }
        main {
            flex-direction: row;
            align-items: flex-end;
            gap: 5rem;

            height: 100%;
            margin: 0;
            padding: 3rem 0 7rem 0;

            text-align: left;
        }
        button {
            width: 17rem;
            height: 17rem;
            margin: 0;
        }
        button:hover {
            box-shadow: rgba(255, 255, 255, 0.1) 0 0 0 5rem;
        }
    }
</style>