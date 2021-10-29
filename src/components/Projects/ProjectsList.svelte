<script>

    import * as projectsData from '../../data/projects.json';
    import ProjectTile from './ProjectTile.svelte';
    import { onMount } from 'svelte';

    export let handleProjectClick;

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

</script>

<ul bind:clientWidth={projectListW}
    style="
        grid-template-columns: repeat({projectXCount}, 1fr);
        grid-gap: {gridGap}rem;
    "
>
    {#if mounted}
        {#each projectsData.default as project}
            <ProjectTile {project} {handleProjectClick} />
        {/each}
    {/if}
</ul>

<style>

    ul {
        height: 100%;
        width: 100%;

        position: relative;
        
        display: grid;
        grid-auto-rows: max-content;
        list-style: none;
    }

</style>