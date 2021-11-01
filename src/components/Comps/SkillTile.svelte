<script>
    export let skill;
    export let isResume;
</script>

<li class:isResume={isResume}>
    {#if skill.logoURL } <img src={skill.logoURL} alt={skill.skill} /> {/if}
    <p>{skill.skill}</p>
</li>

<style>
    li {
        background-color: var(--color-white);
        box-shadow: var(--box-shadow-primary);
        padding: .5rem;
    
        display: flex;
        align-items: center;
        gap: .5rem;

        transition: all .1s;
    }

    li:hover {
        transform: scale(1.05);
    }

    img {
        height: 1.25rem;
    }

    .isResume img {
        height: 2rem !important;
    }

    p {
        white-space: nowrap;
        font-size: var(--font-size-p);
    }
</style>