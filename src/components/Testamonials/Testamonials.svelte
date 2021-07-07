<script>

    import Section from '../Section.svelte';

    export let loaded;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loaded}
    <Section {h} {handleOutroEnd} sectionTitle="Testimony">

    </Section>
{/if}

<style>
</style>