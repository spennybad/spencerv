<script>
    import {send, receive } from '../../util/crossfade';
    import { fade } from 'svelte/transition';
    import SkillTile from '../Projects/SkillTile.svelte';

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
        transition:fade="{{duration: 200}}"
        on:click|self={handleModalClose} 
        id="project_modal" 
        class="centeredInContainer"
    >
        <button on:click={handleModalClose}>X</button>
        <img
            src={clickedProject.imagePath}
            alt={clickedProject.desc}
        >
        <ul id="skill_list">
            {#each clickedProject.stackList as tech}
                <SkillTile {tech}/>
            {/each}
        </ul>
        <p>{clickedProject.desc}</p>x
    </div>
{/if}

<style>
    #project_modal {
        height: 100%;
        width: 100%;
        background-color: var(--color-black-trans90);
        position: fixed;
        box-shadow: var(--box-shadow-light);
        z-index: 101;

        display: grid;
        align-content: center;
        justify-items: center;
        grid-auto-rows: max-content;
    }

    #skill_list {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        list-style: none;
        gap: 1rem;
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
        width: 90%;
        max-width: 40rem;
        border: 2px solid var(--color-white);
        align-self: center;
    }
</style>
 
