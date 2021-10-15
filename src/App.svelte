<script>
    import { onMount } from "svelte";

    // Components 
    import Title from "./components/Title.svelte";
    import Nav from "./components/Navigation/Nav.svelte";
    import Socials from "./components/Socials.svelte";
    import NavToggleButton from "./components/Navigation/NavToggleButton.svelte";

    import About from "./components/About.svelte";
    import Projects from "./components/Projects/Projects.svelte";
    import Experience from "./components/Experience/Experience.svelte";

    let w;
    let h;
    let isNavButtonShown = true;

    $: outroComplete = false;
    $: navPanel = false;

    // 0 == About, 1 == Projects, 2 == Testimonials
    let currentSection = 1;

    $: initial = false;

    onMount(() => {
        initial = true;

        const interval = setInterval(() => {
            initial = false;
            clearInterval(interval);
        }, 1000);
        outroComplete = true;
    });


    // Handlers for syncronus transitions between components.
    const handleOutroEnd = () => {
        outroComplete = true;
    }

    const handleOutroStart = () => {
        outroComplete = false;
    }

    const handleNav = (setto) => {
        if (setto == undefined) {
            navPanel = !navPanel;
        } else {
            navPanel = setto;
        }
    }

    const toggleNavButtonVisibility = () => {
        isNavButtonShown = !isNavButtonShown;
    }


</script>

<main bind:clientWidth={w} bind:clientHeight={h}>
    <Nav {w} loading={initial} bind:currentSection {handleOutroStart} {navPanel} {handleNav} />
    <Socials {initial} {w} />
    
    <header >
        <Title {initial} {w} />
        {#if isNavButtonShown} <NavToggleButton loading={initial} {handleNav}/> {/if}
    </header>

    {#if currentSection == 0 && outroComplete}
        <About loading={initial} {h} {handleOutroEnd} />
    {:else if currentSection == 1 && outroComplete}
        <Projects loading={initial} {h} {handleOutroEnd} {toggleNavButtonVisibility} />
    {:else if currentSection == 2 && outroComplete}
        <Experience loading={initial} {h} {handleOutroEnd} />
    {/if}
</main>

<style>

    /* SITE BREAKING FIX -> In loving memory of Frogman. */
    main {
        position: relative;
        width: 100%;
        min-height: 100vh;
        align-content: center;
        background-color: var(--color-grey-dark);
    }

    header {
        display: flex;
        align-items: center;
        padding: 1rem;
    }

</style>
