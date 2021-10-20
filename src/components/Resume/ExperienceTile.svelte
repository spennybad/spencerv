<script>
    export let experience;

    console.log(experience);
</script>

<li>
    <div>
        <span><h4>{experience.company}</h4><div class="divider" /><p>({experience.dateRange})</p></span>
        <p>{experience.jobTitle}</p>
    </div>
    <p>{experience.jobDesc}</p>
</li>

<style>
    
    li {
        width: 100%;
        background-color: var(--color-grey-light);
        box-shadow: var(--box-shadow-light);
        padding: 1rem;
        color: var(--color-white);

        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    h4 {
        font-size: var(--font-size-h4);
        display: inline;
    }

    div p {
        color: var(--color-primary);
    }

    div span p {
        color: var(--color-white);
    }

    span {
        display: flex;
        width: max-content;
        align-items: center;
        gap: .2rem;
        flex-wrap: wrap;
    }


</style>