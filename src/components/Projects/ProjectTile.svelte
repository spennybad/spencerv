<script>
    export let project;
    export let projectListH;
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
    <div style="background-image: url({project.imagePath})" />
    <div class="projectHoverPanel">
        <a href={project.url}>
            <img src="/images/earth.svg" alt="Internet."/>
        </a>
        <a href={project.git}>
            <img src="/images/github1.svg" alt="Github."/>
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


    div {
        height: 100%;
        width: 100%;

        position: absolute;
        top: 0;
        right: 0;

        background-size: cover;
        background-position: center;
        transition: all .2s;
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
        position: relative;
        height: 100%;
        width: 100%;

        display: grid;
        place-items: center;
        
        transition: all .2s;
    }

    .projectHoverPanel a img {
        filter: invert();
        height: 30%;
        width: 30%;
    }

    .projectHoverPanel a:hover {
        transform: scale(1.1);
    }

    li:hover .projectHoverPanel {
        visibility: visible;
        opacity: 1;
    }

</style>