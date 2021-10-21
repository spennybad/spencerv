<script>
    export let skill;
</script>

<li>
    <img src={skill.logoURL} alt={skill.skill} />
    <p>{skill.skill}</p>
</li>

<style>
    li {
        font-size: var(--font-size-p);
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
        height: 2rem;
    }

    p {
        white-space: nowrap;
    }
</style>