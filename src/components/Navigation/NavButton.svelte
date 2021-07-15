<script>

    import { fly } from "svelte/transition";
    
    export let setCurrentSection;
    export let selection;
    export let w;

</script>

<li 
    in:fly="{{x: w, duration: 200, delay: selection * 100}}"
    out:fly="{{x: w, duration: 200, delay: selection * 100}}"
>
    <button 
        on:click={() => {
                setCurrentSection(selection);
            }}
        >
            <slot />
    </button>
</li>

<style>

    button {
        border: none;
        background-color: var(--color-primary);
        padding: 1rem;
        font-size: var(--font-size-p);
        font-weight: 600;
        transition: all .2s;
        cursor: pointer;
        transition: all .2s;
        margin-right: -2rem; /* In loving memory of P_G_*/
        padding-right: 3rem; 
    }

    button:hover {
        transform: translateX(-2rem);
    }

    li:not(:last-child) {
        margin-bottom: .5rem;
    }

    /* REMOVES MARGIN AND PADDING FOR MOBILE NAVIGATION */
    @media only screen and (max-width: 650px) {
        button {
            padding-right: 1rem;
            margin-right: 0rem;
            font-size: var(--font-size-h4);
            color: var(--color-primary);
            background-color: var(--color-grey-light);
        }

        li:not(:last-child) {
            margin-bottom: 2rem;
        }
        
        button:hover {
            transform: translateX(-.5rem);
        }
    }


</style>