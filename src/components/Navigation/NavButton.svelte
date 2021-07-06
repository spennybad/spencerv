<script>

    import { fly } from "svelte/transition";
    export let setCurrentSection;
    export let selection;
    export let w;

</script>

<li in:fly="{{x: w, duration: 200, delay: selection * 200}}">
    <button on:click={() => setCurrentSection(selection)}><slot /></button>
</li>

<style>

    button {
        border: none;
        background-color: var(--color-primary);
        padding: 1rem;
        font-size: var(--font-size-p);
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


</style>