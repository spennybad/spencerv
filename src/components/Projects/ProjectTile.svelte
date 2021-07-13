<script>
    export let projectListH;
    export let projectListW;
    export let projectXCount;
    
</script>

<li style="
        width: calc({projectListW/projectXCount}px - 2rem);
        height: calc(0.6 * ({projectListW/projectXCount}px - 2rem));
    "
>
    
</li>

<style>
    li {
        background-color: var(--color-white);
    }

</style>