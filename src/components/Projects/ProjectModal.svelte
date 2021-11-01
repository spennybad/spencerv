<script>
    import { fly } from 'svelte/transition';
    import SkillTile from '../Comps/SkillTile.svelte';

    export let clickedProject = undefined;
    export let handleOutroReset;

    let w;

    $: currentId = clickedProject ? clickedProject.id : currentId;

    const handleModalClose = () => {
        clickedProject = null;
        handleOutroReset();
    }

</script>

<svelte:window on:keydown={(event) => {if (clickedProject && event.code == "Escape") handleModalClose()}} />

{#if clickedProject}
    <div 
        bind:clientWidth={w}
        transition:fly="{{x: w, duration: 200}}"
        on:click|self={handleModalClose} 
        id="project_modal" 
        class="centeredInContainer"
    >
        <button 
            on:click={handleModalClose}
            id="exit_button"
        >
            <img
                src={"/images/x.svg"}
                alt={"Exit Icon."}
            >
        </button>
        <a
            href={clickedProject.url}
            target="_blank"
            id="image_hover"
        >
            <img
                src={clickedProject.imagePath}
                alt={clickedProject.desc}
                id="project_img"
            >
        </a>
        <ul id="skill_list">
            {#each clickedProject.stackList as skill}
                <SkillTile isResume={false} {skill}/>
            {/each}
        </ul>
        <p>{clickedProject.desc}</p>
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
        gap: 3rem;
    }

    #skill_list {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        list-style: none;
        gap: 1rem;
    }

    #exit_button {
        position: absolute;
        top: 0;
        right: 0;
        margin: 1rem;
        border: none;
        background-color: transparent;
        appearance: none;

        height: 2rem;
        width: 2rem;

        font-size: var(--font-size-p);
        border-radius: 100%;
        cursor: pointer;
        filter: invert();
        transition: all .2s;
    }

    #exit_button:hover {
        transform: scale(0.90);
    }

    #image_hover {
        position: relative;
        width: 90%;
        max-width: 40rem;
        overflow: hidden;
    }
    
    #project_img {
        height: auto;
        width: 100%;
        border: 2px solid var(--color-white);
    }

    p {
        font-size: var(--font-size-p);
        color: var(--color-white);
        text-align: center;
    }
</style>
 
