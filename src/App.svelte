<script>
    import { onMount } from "svelte";

    // Components 
    import Title from "./components/Title.svelte";
    import Nav from "./components/Navigation/Nav.svelte";
    import Socials from "./components/Socials.svelte";
    import NavToggleButton from "./components/Navigation/NavToggleButton.svelte";

    import About from "./components/About.svelte";
    import Projects from "./components/Projects/Projects.svelte";
    import Testamonials from "./components/Testamonials/Testamonials.svelte";

    let w;
    let h;

    $: outroComplete = false;
    $: navPanel = false;

    // 0 == About, 1 == Projects, 2 == Testimonials
    let currentSection = 0;

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

</script>

<main bind:clientWidth={w} bind:clientHeight={h}>
    <Nav {w} loading={initial} bind:currentSection {handleOutroStart} {navPanel} {handleNav} />

    <header>
        <Title {initial} {w} />
        <div id="navAndSocials">
            <NavToggleButton loading={initial} {handleNav}/>
            <Socials {initial} {w} />
        </div>
    </header>

    {#if currentSection == 0 && outroComplete}
        <About loading={initial} {h} {handleOutroEnd} />
    {:else if currentSection == 1 && outroComplete}
        <Projects loading={initial} {h} {handleOutroEnd} />
    {:else if currentSection == 2 && outroComplete}
        <Testamonials loading={initial} {h} {handleOutroEnd} />
    {/if}
</main>

<style>

    main {
        position: relative;
        width: 100%;
        height: 100%;
        align-content: center;
        background-color: var(--color-grey-dark);

        display: grid;
        grid-template-rows: 10% 90%;

        overflow: hidden;
    }

    header {
        display: flex;
        align-items: center;
        padding: 1rem;
    }

    #navAndSocials {
        position: relative;
        margin-left: auto;
    }

</style>
