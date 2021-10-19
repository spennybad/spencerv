<script>
    import { fly } from "svelte/transition";
    import Socials from "./Socials.svelte";

    // Props
    export let sectionTitle;
    export let loading;
    export let w;    
    export let h;
    export let handleOutroEnd;

</script>

<section 
    transition:fly="{{y: h, duration: 200}}" 
    on:outroend="{handleOutroEnd}"
>   
    <aside>      
        <h2>{sectionTitle}</h2>
        <Socials {loading} />
    </aside>
    <slot />
</section>

<style>
    section {
        width: 100%;
        height: 100%;
    
        position: relative;
        z-index: 0;
        display: grid;
        grid-template-columns: auto 1fr;
    }

    aside {
        height: 100%;
        display: grid;
        grid-template-rows: auto 1fr;
        align-items: end;
        justify-items: center;
    }

    h2 {
        font-size: var(--font-size-h2);
        white-space: nowrap;
        writing-mode: vertical-rl; 
        text-orientation: mixed;
        line-height: 1;
        z-index: -1;
        color: var(--color-primary-trans50);
        margin-bottom: auto;
    }
</style>