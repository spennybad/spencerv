<script>
    import {send, receive } from '../../util/crossfade';

    export let clickedProject = undefined;
    export let handleOutroReset;

    $: currentId = clickedProject ? clickedProject.id : currentId;

    const handleModalClose = () => {
        clickedProject = null;
        handleOutroReset();
    }

</script>

{#if clickedProject}
    <div 
        on:click|self={handleModalClose} id="project_modal" class="centeredInContainer">
        <img
            src={clickedProject.imagePath}
            in:receive="{{key:clickedProject.id}}"
            out:send="{{key:currentId}}"
            alt={clickedProject.desc}
        />
        <button on:click={handleModalClose}>X</button>
    </div>
{/if}


<style>
    #project_modal {
        height: 100%;
        width: 100%;
        background-color: var(--color-black-trans75);
        position: fixed;
        box-shadow: var(--box-shadow-light);
        z-index: 101;

        display: grid;
        grid-template-columns: repeat(2, 1fr);
        place-items: center;

    }

    button {
        position: absolute;
        top: 0;
        right: 0;
        margin: 1rem;
        border: none;
        background-color: var(--color-primary);

        height: 2rem;
        width: 2rem;

        font-size: var(--font-size-p);
        border-radius: 100%;
        cursor: pointer;
    }

    img {
        height: auto;
        width: 70%;
    }
</style>

