<script>
    export let tech;
</script>

<li>
    <p>{tech}</p>
</li>

<style>
    li {
        font-size: var(--font-size-p);
        background-color: var(--color-white);
        box-shadow: var(--box-shadow-primary);
        padding: .5rem;
    }

    p {
        white-space: nowrap;
    }
</style>