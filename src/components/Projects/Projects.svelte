<script>

    import Section from '../Comps/Section.svelte';
    import ProjectList from './ProjectsList.svelte';
    import ProjectModal from './ProjectModal.svelte';

    export let loading;
    export let handleOutroEnd;
    export let h;
    export let toggleNavButtonVisibility;
    export let toggleNavVisibility;

    const handleOutroReset = () => {
        toggleNavButtonVisibility();
        toggleNavVisibility();
    }

    let clickedProject;

    const handleProjectClick = (project) => {
        clickedProject = project;
        toggleNavButtonVisibility();
        toggleNavVisibility();
    }

</script>

{#if !loading}
    <Section 
        {h} 
        {loading}
        {handleOutroEnd}  
        sectionTitle="Projects" 
    >
        <ProjectList {handleProjectClick} />
        <ProjectModal bind:clickedProject {handleOutroReset} />
    </Section>
{/if}

<style>
</style>