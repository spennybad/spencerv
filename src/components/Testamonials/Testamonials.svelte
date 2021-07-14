<script>

    import Section from '../Section.svelte';

    export let loading;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loading}
    <Section {h} {handleOutroEnd} sectionTitle="Testimony">

    </Section>
{/if}

<style>
</style>