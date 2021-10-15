<script>
    import NavButton from './NavButton.svelte';
    import { fly } from 'svelte/transition';

    export let currentSection;
    export let loading;
    export let handleOutroStart;
    export let navPanel;
    export let handleNav;

    export let w;

    const setCurrentSection = (selection) => {
        handleNav(false);
        if (selection != currentSection) {
            currentSection = selection;
            handleOutroStart(selection);
        }
    }

    $: if (w > 650) {
        handleNav(false);
    }

</script>

{#if !loading}
    {#if navPanel}
        <nav id="mobile_nav" transition:fly="{{x: w, duration: 100}}">
            <ul>
                <NavButton {w} {currentSection} selection={0} {setCurrentSection} >About</NavButton>
                <NavButton {w} {currentSection} selection={1} {setCurrentSection} >Projects</NavButton>
                <NavButton {w} {currentSection} selection={2} {setCurrentSection} >Experience</NavButton>
            </ul>
        </nav>
    {/if}
    <nav id="desktop_nav">
        <ul>
            <NavButton {w} {currentSection} selection={0} {setCurrentSection} >About</NavButton>
            <NavButton {w} {currentSection} selection={1} {setCurrentSection} >Projects</NavButton>
            <NavButton {w} {currentSection} selection={2} {setCurrentSection} >Experience</NavButton>
        </ul>
    </nav>
{/if}

<style>

    nav {
        position: fixed;
    }

    #desktop_nav {
        top: 50%;
        right: 0;
        transform: translateY(-50%);
        z-index: 1; /* SITE BREAKING FIX - Love: P_G_*/
    }

    #desktop_nav ul {
        list-style: none;
        text-align: right;
    }


    #mobile_nav {
        visibility: hidden;
        top: 0;
        right: 0;
        height: 100%;
        width: 100%;
        background-color: var(--color-black-trans90);
        display: grid;
        place-items: center;
        z-index: 1;
    }

    #mobile_nav ul {
        list-style: none;
        text-align: center;
    }
    

    @media only screen and (max-width: 650px) {
        #mobile_nav {
            visibility: visible;
        }

        #desktop_nav {
            visibility: hidden;
        }
    }

</style>