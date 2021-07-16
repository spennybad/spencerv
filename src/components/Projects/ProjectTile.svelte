<script>
    export let project;
    export let projectListW;

    export let projectXCount;
    export let gridGap;
</script>

<li style="
        width: calc({projectListW/projectXCount}px - {gridGap}rem);
        height: calc(0.6 * ({projectListW/projectXCount}px - {gridGap}rem));
    "
    class:priority={project.priority}
>  
    <img class="background_image" src={project.imagePath} alt="Project." />
    <div class="projectHoverPanel">
        <a href={project.url}>
            <img src="/images/earth.svg" alt="Internet."/>
            <p>Visit Site</p>
        </a>
        <a href={project.git}>
            <img src="/images/github1.svg" alt="Github."/>
            <p>Visit Repo</p>
        </a>
    </div>
</li>

<style>

    li {
        background-color: var(--color-white);
        position: relative;
        height: 100%;
        width: 100%;
        overflow: hidden;
        box-shadow: var(--shadow-light);
        border: 2px solid transparent;
        transition: all .2s;
    }

    li.priority:after {
        content: "*";
        position: absolute;
        top: 0;
        right: 0;
        font-size: var(--font-size-h1);
        line-height: .8;
        color: var(--color-accent);
        padding: .5rem;
        text-shadow: 1px 1px 2px var(--color-black-trans75);
    }


    .background_image {
        height: 100%;
        width: 100%;

        object-fit: cover;
    }

    li:hover {
        border: 2px solid var(--color-primary);
    }

    li:hover div {
        transform: scale(1.1);
    }

    .projectHoverPanel {
        position: absolute;
        top: 0;
        left: 0;

        height: 100%;
        width: 100%;

        background-color: var(--color-black-trans75);
        visibility: hidden;
        opacity: 0;

        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-auto-rows: 100%;
        place-items: center;

        transition: all .2s;
    }

    .projectHoverPanel a {
        display: grid;
        place-items: center;
        
        transition: all .2s;
    }

    a { 
        text-decoration: none;
        appearance: none;
    }

    .projectHoverPanel a p {
        margin-top: .5rem;
        background-color: var(--color-grey-dark);
        color: var(--color-primary);
        padding: .25rem;
        border: none;
    }

    .projectHoverPanel a img {
        filter: invert();
        height: 100%;
        width: 100%;
    }

    .projectHoverPanel a:hover {
        transform: scale(1.1);
    }

    li:hover .projectHoverPanel {
        visibility: visible;
        opacity: 1;
    }

</style>