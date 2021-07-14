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
        styling="padding: 0rem 6rem 0rem 6rem;"
    >
        <ProjectList />
    </Section>
{/if}

<style>
</style>