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
</li>

<style>

    li {
        background-color: var(--color-white);
        position: relative;
        overflow: hidden;
        box-shadow: var(--shadow-light);
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
        background-size: cover;
        background-position: center;
        transition: all .2s;
    }

    div:hover {
        transform: scale(1.1);
    }

</style>