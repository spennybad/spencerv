<script>

    import ExperienceTile from './ExperienceTile.svelte';

    export let experienceData;

</script>

<div>
    <h3>Experience</h3>
    <ul>
        {#each experienceData.default as experience}
            <ExperienceTile {experience} />
        {/each}
    </ul>    
</div>

<style>

    div {
        grid-column: 1 / 3;
    }

    ul {
        display: flex;
        flex-direction: column;
        gap: .5rem;
        list-style: none;
        height: 100%;
    }

    @media only screen and (max-width: 1100px) {
        div {
            grid-column: unset;
        }
    }

</style>