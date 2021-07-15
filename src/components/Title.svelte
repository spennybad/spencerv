<script>
    import { fly } from "svelte/transition";

    export let w;
    export let initial;

</script>

{#if initial}
    <h1
        class="centeredInContainer"
        in:fly={{ x: -w, duration: 400 }}
        out:fly={{ x: w, duration: 400 }}
    >
        Spencer Venable
    </h1>
{:else}
    <h1 in:fly={{ x: -w, duration: 200 }}>Spencer Venable</h1>
{/if}

<style>

    h1 {
        font-size: var(--font-size-h1);
        color: var(--color-white);
        white-space: nowrap;
    }
</style>
