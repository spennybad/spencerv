<script>

    import Section from '../Section.svelte';
    import ProjectList from './ProjectsList.svelte';

    export let loading;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loading}
    <Section 
        {h} 
        {handleOutroEnd} 
        sectionTitle="Projects" 
        styling="projects"
    >
        <ProjectList />
    </Section>
{/if}

<style>
</style>