<script>
    import { fly } from "svelte/transition";

    // Props
    export let sectionTitle;
    export let h;
    export let handleOutroEnd;
    export let styling;
</script>

<section 
    in:fly="{{y: h, duration: 200}}" 
    out:fly="{{y: h, duration: 200}}"
    on:outroend="{handleOutroEnd}"
    style={styling}
>
    <h2>{sectionTitle}</h2>
    <slot></slot>
</section>

<style>
    section {
        width: 100%;
        height: 100%;
        max-height: 100vh;
        padding: 6rem;
        position: relative;
        z-index: 0;
        display: grid;
        grid-template-columns: 100%;
    }

    h2 {
        position: absolute;
        font-size: var(--font-size-h2);
        white-space: nowrap;
        line-height: 1;
        transform-origin: bottom left;
        transform: rotate(90deg) translateX(-20%);
        top: 0;
        z-index: -1;

        color: var(--color-primary-trans50);
    }
    
</style>