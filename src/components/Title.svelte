<script>
    import { fly } from "svelte/transition";

    export let w;
    export let h;
    export let initial;

</script>

{#if initial}
    <h1
        id="title_initial"
        class="centeredInContainer"
        in:fly={{ x: -w, duration: 400 }}
        out:fly={{ x: w, duration: 400 }}
    >
        Spencer Venable
    </h1>
{:else}
    <h1 in:fly={{ x: -w, duration: 300 }} id="title">Spencer Venable</h1>
{/if}

<style>
    #title_initial {
        color: var(--color-white);
        font-size: var(--font-size-h1);
        white-space: nowrap;
    }

    #title {
        color: var(--color-white);
    }
</style>
