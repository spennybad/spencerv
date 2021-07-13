<script>
    import ProjectTile from './ProjectTile.svelte';

    let projectListW;
    let projectListH;
    let projectXCount = 2;

</script>

<ul bind:clientWidth={projectListW} bind:clientHeight={projectListH}
    style="grid-template-columns: repeat({projectXCount}, 1fr);"
>
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
    <ProjectTile {projectListW} {projectListH} {projectXCount} />
</ul>

<style>

    ul {
        height: 100%;
        width: 100%;

        position: relative;
        
        display: grid;
        grid-gap: 2rem;
        justify-content: center;
        grid-auto-rows: max-content;
        list-style: none;
        padding: 1rem;
        
        overflow-y: scroll;
    }
</style>