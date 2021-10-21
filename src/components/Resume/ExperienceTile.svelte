<script>
    export let experience;

    console.log(experience);
</script>

<li>
    <div>
        <div><h4>{experience.company}</h4><p>({experience.dateRange})</p></div>
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
        transition: all .2s;
    }

    li:hover {
        transform: translateX(-.5rem);
    }

    h4 {
        font-size: var(--font-size-h4);
        display: inline;
    }

    div p {
        color: var(--color-primary);
    }

    div div {
        display: flex;
        align-items: center;
        gap: .5rem;
        flex-wrap: wrap;
    }

    div div p {
        color: var(--color-white);
    }


</style>