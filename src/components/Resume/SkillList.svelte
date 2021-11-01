<script>
    import SkillTile from '../Comps/SkillTile.svelte';

    export let skills;
    export let level;

</script>

<ul

>
    {#each skills as skill}
        <SkillTile isResume={true} skill={skill} />
    {/each}
    <p>{level}</p>
</ul>

<style>

    ul {
        position: relative;
        width: 100%;
        list-style: none;
        display: flex;
        gap: 1rem;
        flex-wrap: wrap;
        padding: 2rem 1rem 1rem 1rem;
        margin-top: 1rem;
        box-shadow: -3px 0px 0px var(--color-primary);
    }

    p {
        position: absolute;
        top: 0;
        left: 0;
        color: var(--color-white-trans75);
        text-transform: uppercase;
        font-size: var(--font-size-p);
        font-weight: 600;
        margin-left: 1rem;
    }

</style>