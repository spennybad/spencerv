<script>

    import * as projectsData from '../../data/projects.json';
    import ProjectTile from './ProjectTile.svelte';
    import { onMount } from 'svelte';

    export let handleProjectClick;

    let mounted = false;
    
    let projectListW;

    const gridBreakPoints = {
        1000: 1,
        10000: 2
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
        gap: .5rem;
        grid-auto-rows: max-content;
        list-style: none;
        padding: 0 .5rem .5rem 0rem;
    }

</style>