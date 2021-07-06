<script>
    import { fade } from "svelte/transition";

    // Props
    export let sectionTitle;
</script>

<section in:fade>
    <h2 in:fade>{sectionTitle}</h2>
    <slot></slot>
</section>

<style>
    section {
        width: 100%;
        height: 100%;
        padding: 6rem;
        position: relative;
        z-index: 0;
        
        display: grid;
        justify-content: center;

        grid-template-columns: 40%;

    }

    h2 {
        position: absolute;
        font-size: var(--font-size-h2);
        white-space: nowrap;
        line-height: 1;
        transform-origin: bottom left;
        transform: rotate(90deg) translateX(-20%);
        top: 0;
        z-index: -1;

        color: var(--color-primary-trans50);
    }
    
    @media only screen and (max-width: 1499px) {
        section {
            grid-template-columns: 50%;
        }
    }

    
    @media only screen and (max-width: 1100px) {
        section {
            grid-template-columns: 60%;
        }
    }
    
    @media only screen and (max-width: 800px) {
        section {
            grid-template-columns: 80%;
        }
    }
    
</style>