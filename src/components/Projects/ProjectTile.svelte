<script>

    export let project;

    export let handleProjectClick;

</script>

<li 
    on:click={() => handleProjectClick(project)}
>  
    <img class="background_image" src={project.imagePath} alt="Project." />
</li>

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