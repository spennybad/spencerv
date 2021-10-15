<script>

    import * as projectsData from '../../data/projects.json';
    import ProjectTile from './ProjectTile.svelte';
    import { onMount } from 'svelte';

    export let handleProjectClick;
    export let outroEnded;

    let mounted = false;
    
    let projectListW;
    let gridGap = 1;

    const gridBreakPoints = {
        600: 1,
        1000: 2,
        1600: 3,
        10000: 4
    }

    const getXCount = (w, gridBreakPoints) => {
        for (let breakpoint in gridBreakPoints) {
            if (w < breakpoint) {
                return gridBreakPoints[breakpoint];
            }
        }
        return 1;
    }

    $: projectXCount = getXCount(projectListW, gridBreakPoints);

    // Fixes content shift of projects being loaded.
    onMount(() => {
        mounted = true;
    })

    const handleOutroEnded = () => {
        outroEnded = true;
    }

</script>

<ul bind:clientWidth={projectListW}
    style="
        grid-template-columns: repeat({projectXCount}, 1fr);
        grid-gap: {gridGap}rem;
        padding: calc({gridGap}rem + 1rem);
    "
>
    <p><span>*</span>  denotes key project.</p>
    {#if mounted}
        {#each projectsData.default as project}
            <ProjectTile {project} {projectListW} {projectXCount} {gridGap} {handleProjectClick} {handleOutroEnded} />
        {/each}
    {/if}
</ul>

<style>

    ul {
        height: 100%;
        width: 100%;

        position: relative;
        
        display: grid;
        justify-self: center;
        justify-content: center;
        grid-auto-rows: max-content;
        list-style: none;
    }

    p {
        position: absolute;
        top: 0;
        right: 0;
        color: var(--color-white);
        display: flex;
        font-size: var(--font-size-p);
    }

    p span {
        color: var(--color-accent);
    }

    @media only screen and (max-width: 1000px) {
        ul {
            width: 80%;
        }
    }

    @media only screen and (max-width: 650px) {
        ul {
            width: 80%;
        }
    }

</style>