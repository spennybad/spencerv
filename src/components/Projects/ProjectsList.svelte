<script>

    import * as projectsData from '../../data/projects.json';
    import ProjectTile from './ProjectTile.svelte';
    let projectListW;
    let projectListH;

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

    console.log(projectsData);

</script>

<ul bind:clientWidth={projectListW} bind:clientHeight={projectListH}
    style="
        grid-template-columns: repeat({projectXCount}, 1fr);
        grid-gap: {gridGap}rem;
        padding: calc({gridGap}rem + 1rem);
    "
>
    <p><span>*</span> denotes key project.</p>
    {#each projectsData.default as project}

        <ProjectTile {project} {projectListW} {projectListH} {projectXCount} {gridGap} />

    {/each}

</ul>

<style>

    ul {
        height: 100%;
        width: 90%;

        position: relative;
        
        display: grid;
        justify-self: center;
        justify-content: center;
        grid-auto-rows: max-content;
        list-style: none;
        overflow-y: scroll;
    }

    p {
        position: absolute;
        top: 0;
        right: 0;
        color: var(--color-white);
        display: flex;
    }

    p span {
        font-size: var(--font-size-h4);
        color: var(--color-accent);
        line-height: 1;
        margin-right: .5rem;
    }
    
</style>