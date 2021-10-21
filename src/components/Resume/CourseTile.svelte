<script>

    export let course;

</script>

<li>
    <a href={course.url} target="_blank">
        <div>
            <h4>{course.title}</h4>
            <img src="/images/udemy.svg" alt="temp" />
        </div>
        <p>{course.desc}</p>
    </a>
</li>

<style>

    li {
        background-color: var(--color-grey-light);
        box-shadow: var(--box-shadow-light);
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 1rem;
        position: relative;
        cursor: pointer;
        padding-bottom: 2rem;
        overflow: hidden;
        transition: all .2s;
    }

    li:after {
        content: "See More";
        font-size: var(--font-size-p);
        color: var(--color-white-trans75);
        text-transform: uppercase;

        position: absolute;
        bottom: 0;
        right: 0;
        line-height: 1;
    }

    li:hover {
        transform: translateX(-.5rem);
    }

    li:hover:after {
        color: var(--color-primary);
    }

    h4 {
        font-size: var(--font-size-p);
        color: var(--color-white);
    }

    p {
        color: var(--color-primary);
    }

    a {
        text-decoration: none;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    div

    img {
        position: absolute;
        top: 0;
        right: 0;
        height: 2rem;
        width: 2rem;
        margin: .5rem;
    }

</style>