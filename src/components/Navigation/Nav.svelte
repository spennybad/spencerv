<script>
    import NavButton from './NavButton.svelte';

    export let currentSection;
    export let loaded;
    export let handleOutroStart;

    export let w;

    const setCurrentSection = (selection) => {
        if (selection != currentSection) currentSection = selection;
    }

</script>

{#if !loaded}
    <nav>
        <ul>
            <NavButton {w} {currentSection} selection={0} {setCurrentSection} {handleOutroStart}>About</NavButton>
            <NavButton {w} {currentSection} selection={1} {setCurrentSection} {handleOutroStart}>Projects</NavButton>
            <NavButton {w} {currentSection} selection={2} {setCurrentSection} {handleOutroStart}>Testimony</NavButton>
        </ul>
    </nav>
{/if}

<style>

    nav {
        position: absolute;
        top: 50%;
        right: 0;
        transform: translateY(-50%);
        z-index: 1; /* SITE BREAKING FIX - Love: P_G_*/
    }

    ul {
        list-style: none;
        text-align: right;
    }


</style>