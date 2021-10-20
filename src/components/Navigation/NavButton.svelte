<script>

    import { fly } from "svelte/transition";
    
    export let setCurrentSection;
    export let selection;
    export let w;

</script>

<li 
    in:fly="{{x: w, duration: 200, delay: selection * 100}}"
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
        background-color: var(--color-white);
        color: var(--color-black);
        padding: 1rem;
        font-size: var(--font-size-p);
        cursor: pointer;
        transition: all .2s;
        padding-right: 3rem; 
        transform: translateX(2rem);
        box-shadow: var(--box-shadow-primary);
    }

    /* In loving memory of Kn4ppster + FrogmanOW <3 */
    button:hover {
        transform: translateX(0rem);
    }

    li:not(:last-child) {
        margin-bottom: .5rem;
    }


</style>