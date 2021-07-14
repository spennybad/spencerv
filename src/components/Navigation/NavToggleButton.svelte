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
        appearance: none;
        border: none;
        margin-left: auto;

        width: 3rem;

        display: grid;
        grid-template-rows: repeat(3, max-content);;
        place-items: center;
        gap: .4rem;

        background: none;
        visibility: hidden;

        z-index: 10;

        cursor: pointer;
    }

    div {
        height: .2rem;
        width: 100%;
        background-color: var(--color-primary);
    }
        
    @media only screen and (max-width: 650px) {
        button {
            visibility: visible;
        }
    }

</style>