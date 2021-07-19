<script>

    import Section from '../Section.svelte';
    import ProjectList from './ProjectsList.svelte';
    import ProjectModal from './ProjectModal.svelte';

    export let loading;
    export let handleOutroEnd;
    export let h;
    export let toggleNavButtonVisibility;

    let outroEnded = false;

    const handleOutroReset = () => {
        outroEnded = false;
        toggleNavButtonVisibility();
    }

    let clickedProject;

    const handleProjectClick = (project) => {
        clickedProject = project;
        toggleNavButtonVisibility();
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