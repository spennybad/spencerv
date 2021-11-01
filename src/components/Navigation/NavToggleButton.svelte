<script>
    export let loading;
    export let handleNav;
    export let w;

    import { fly } from "svelte/transition";
</script>


{#if !loading}
    <button 
        transition:fly={{x: w, duration: 400}}
        on:click={() => handleNav()}
    >
        <div />
        <div />
        <div />
    </button>
{/if}


<style>

    button {
        position: relative;

        border: none;

        margin-left: auto;

        width: 2.5rem;

        display: grid;
        grid-template-rows: repeat(3, max-content);;
        place-items: center;
        gap: .4rem;

        background: none;

        z-index: 101;

        cursor: pointer;
    }

    div {
        height: .2rem;
        width: 100%;
        background-color: var(--color-primary);
    }

</style>