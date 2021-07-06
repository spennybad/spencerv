<script>
    import NavButton from './NavButton.svelte';

    export let currentSection;
    export let loaded;

    export let w;

    const setCurrentSection = (selection) => {
        currentSection = selection
    }

</script>

{#if !loaded}
    <nav>
        <ul>
            <NavButton {w} selection={0} {setCurrentSection}>About</NavButton>
            <NavButton {w} selection={1} {setCurrentSection}>Projects</NavButton>
            <NavButton {w} selection={2} {setCurrentSection}>Testimonials</NavButton>
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