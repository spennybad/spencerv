<script>
    import NavButton from './NavButton.svelte';
    import { fly } from 'svelte/transition';

    export let currentSection;
    export let loading;
    export let handleOutroStart;
    export let navPanel = false;
    export let handleNav;

    export let w;

    const setCurrentSection = (selection) => {
        handleNav(false);
        if (selection != currentSection) {
            currentSection = selection;
            handleOutroStart(selection);
        }
    }

    const pages = ["Home", "Resume", "Projects"]

</script>

<svelte:window on:keydown={(event) => {if (navPanel && event.code == "Escape") setCurrentSection(currentSection)}} />

{#if !loading}
    {#if navPanel}
        <nav 
            transition:fly="{{x: w, duration: 100}}"
            on:click|self={() => setCurrentSection(currentSection)}
        >
            <ul>
                {#each pages as page, index}
                    <NavButton {w} selection={index} {setCurrentSection} >{page}</NavButton>
                {/each}
            </ul>
        </nav>
    {/if}
{/if}

<style>

    nav {
        position: fixed;
        top: 0;
        right: 0;
        height: 100%;
        width: 100%;
        background-color: var(--color-black-trans90);
        display: grid;
        justify-items: end;
        align-items: center;
        z-index: 1;
    }

    nav ul {
        list-style: none;
        text-align: end;
    }


    
</style>