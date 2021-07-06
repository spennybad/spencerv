<script>
    import { onMount } from "svelte";

    // Components 
    import Title from "./components/Title.svelte";
    import About from "./components/About.svelte";
    import Socials from "./components/Socials.svelte";
    import Nav from "./components/Navigation/Nav.svelte";

    let w;
    let h;

    // 0 == About, 1 == Projects, 2 == Testimonials
    let currentSection = "0"

    $: initial = false;

    onMount(() => {
        initial = true;

        const interval = setInterval(() => {
            initial = false;
            clearInterval(interval);
        }, 1000);
    });

</script>

<main bind:clientWidth={w} bind:clientHeight={h}>
    <Nav {w} loaded={initial} bind:currentSection />
    
    <header>
        <Title {initial} {w} {h} />
        <Socials />
    </header>

    {#if currentSection == 0}
        <About loaded={initial} {w} {h} />
    {:else if currentSection == 1}
        <p>temp</p>
    {:else if currentSection == 2}
        <p>temp</p>
    {/if}
</main>

<style>

    header {
        display: flex;
        align-items: center;
        padding: 1rem;
    }

    main {
        position: relative;
        width: 100%;
        height: 100%;
        align-content: center;
        background-color: var(--color-grey-dark);
        overflow: hidden;

        display: grid;
        grid-template-rows: auto 1fr;
    }
</style>
