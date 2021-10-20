<script>

    import CourseTile from './CourseTile.svelte';

    export let courseData;

</script>

<div>
    <h3>Courses</h3>
    <ul>
        {#each courseData.default as course}
            <CourseTile {course} />
        {/each}
    </ul>
</div>


<style>
    ul {
        display: flex;
        flex-direction: column;
        list-style: none;
        gap: .5rem;
    }
</style>