<script>

    import Section from '../Section.svelte';
    import ProjectList from './ProjectsList.svelte';
    import ProjectModal from './ProjectModal.svelte';

    export let loading;
    export let handleOutroEnd;
    export let h;

    let outroEnded = false;

    const handleOutroReset = () => {
        outroEnded = false;
    }

    let clickedProject;

    const handleProjectClick = (project) => {
        clickedProject = project;
    }

</script>

{#if !loading}
    <Section 
        {h} 
        {handleOutroEnd}  
        sectionTitle="Projects" 
        styling="projects"
    >
        <ProjectList {handleProjectClick} {clickedProject} bind:outroEnded />
        <ProjectModal bind:clickedProject {handleOutroReset} />
    </Section>
{/if}

<style>
</style>