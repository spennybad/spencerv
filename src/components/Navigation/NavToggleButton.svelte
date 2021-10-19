<script>
    export let loading;
    export let handleNav;
</script>


{#if !loading}
    <button on:click={() => handleNav()}>
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