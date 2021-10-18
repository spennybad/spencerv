<script>
    import { fly } from "svelte/transition";

    // Props
    export let sectionTitle;
    export let h;
    export let handleOutroEnd;
    export let styling = null;

</script>

<section 
    in:fly="{{y: h, duration: 200}}" 
    out:fly="{{y: h, duration: 200}}"
    on:outroend="{handleOutroEnd}"
    class={styling}
>
    <h2>{sectionTitle}</h2>
    <slot />
</section>

<style>
    section {
        width: 100%;
        height: 100%;
        padding: 3rem 10rem;
        position: relative;
        z-index: 0;
        display: grid;
        grid-template-columns: 100%;
    }

    h2 {
        position: absolute;
        font-size: var(--font-size-h2);
        white-space: nowrap;
        line-height: 1;
        writing-mode: vertical-rl; 
        text-orientation: mixed;
        z-index: -1;
        left: 0;
        top: 0;
        color: var(--color-primary-trans50);
    }
    
    /* Amp == Transh */
    
    @media only screen and (max-width: 1000px) {
        section {
            padding: 0rem 7rem;
        }

        .about {
            padding: 3rem 7rem;
        }
    }

    @media only screen and (max-width: 650px) {
        section {
            padding: 0rem 1rem 0rem 6rem;
        }

        .about {
            padding: 3rem 1rem;
        }

        h2 {
            font-size: 4.5rem;
        }

    }


    @media only screen and (max-width: 450px) {
        section {
            padding: 0rem .5rem 0rem 4rem;
        }

        h2 {
            font-size: 4rem;
        }
    }
    
</style>