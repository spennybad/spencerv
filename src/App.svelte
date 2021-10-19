<script>
    import { onMount } from "svelte";

    // Components 
    import Title from "./components/Title.svelte";
    import Nav from "./components/Navigation/Nav.svelte";
    import NavToggleButton from "./components/Navigation/NavToggleButton.svelte";

    import Home from "./components/Home.svelte";
    import Projects from "./components/Projects/Projects.svelte";
    import Resume from "./components/Resume/Resume.svelte";

    let w;
    let h;
    let isNavButtonShown = true;

    $: outroComplete = false;
    $: navPanel = false;
    $: showNav = true;

    // 0 == Home, 1 == About Me, 2 == Projects
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

    const toggleNavVisibility = () => {
        showNav = !showNav;
    }
</script>

<main bind:clientWidth={w} bind:clientHeight={h}>
    <Nav {w} loading={initial} bind:currentSection {handleOutroStart} {navPanel} {handleNav} />
    <header >
        <Title {initial} {w} />
        {#if isNavButtonShown} <NavToggleButton loading={initial} {handleNav}/> {/if}
    </header>

    {#if currentSection == 0 && outroComplete}
        <Home loading={initial} {h} {handleOutroEnd} />
    {:else if currentSection == 1 && outroComplete}
        <Resume loading={initial} {h} {handleOutroEnd} />
    {:else if currentSection == 2 && outroComplete}
        <Projects loading={initial} {h} {handleOutroEnd} {toggleNavButtonVisibility} {toggleNavVisibility}/>
    {/if}
</main>

<style>

    main {
        position: relative;

        width: 100%;
        min-height: 100vh;

        background-color: var(--color-grey-dark);
        overflow: hidden;

        display: grid;
        grid-template-rows: auto 1fr;
    }

    header {
        display: flex;
        align-items: center;
        padding: 1rem;
    }

</style>
