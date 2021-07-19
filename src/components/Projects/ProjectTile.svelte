<script>
    import { onDestroy } from 'svelte';

    export let project;
    export let projectListW;

    export let projectXCount;
    export let gridGap;
    export let handleProjectClick;
    export let placeHolder;
    export let handleOutroEnded;

    import {send, receive } from '../../util/crossfade';

    onDestroy(() => {
        if (placeHolder === false) handleOutroEnded();
    })
    
</script>

{#if !placeHolder}
    <li 
        in:receive="{{key:project.id, duration: 0}}"
        out:send="{{key:project.id, duration: 0}}"
        on:click={() => handleProjectClick(project)}
        style="
            width: calc({projectListW/projectXCount}px - {gridGap}rem);
            height: calc(0.6 * ({projectListW/projectXCount}px - {gridGap}rem));
        "
        class:priority={project.priority}
    >  
        <img class="background_image" src={project.imagePath} alt="Project." />
    </li>
{:else}
    <li 
        style="
            width: calc({projectListW/projectXCount}px - {gridGap}rem);
            height: calc(0.6 * ({projectListW/projectXCount}px - {gridGap}rem));
        "
    >
        <img class="background_image" src={project.imagePath} alt="Project." />
    </li>
{/if}

<style>

    li {
        background-color: var(--color-white);
        position: relative;
        height: 100%;
        width: 100%;
        overflow: hidden;
        box-shadow: var(--shadow-light);
        border: 2px solid transparent;
        transition: all .2s;

        cursor: pointer;
    }

    li.priority:after {
        content: "*";
        position: absolute;
        top: 0;
        right: 0;
        font-size: var(--font-size-h1);
        line-height: .8;
        color: var(--color-accent);
        padding: .5rem;
        text-shadow: 1px 1px 2px var(--color-black-trans75);
    }


    .background_image {
        height: 100%;
        width: 100%;

        object-fit: cover;
        transition: all .2s;
    }

    .background_image:hover {
        transform: scale(1.1);
    }
    

    li:hover {
        border: 2px solid var(--color-primary);
    }

</style>