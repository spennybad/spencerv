<script>
    import { fly } from 'svelte/transition';

    export let initial;
    export let w; 

</script>

{#if !initial}
    <ul class="socials" transition:fly={{x: w, duration: 200}}>
        <li>
            <a href="https://www.linkedin.com/in/spencer-venable-31494a187">
                <img class="centeredInContainer" src="/images/linkedin.svg" alt="LinkedIn">
            </a>
        </li>
        <li>
            <a href="https://github.com/Spencercv7/aim-trainer">
                <img class="centeredInContainer" src="/images/github.svg" alt="GitHub">
            </a>
        </li>
    </ul>
{/if}

<style>
    .socials {
        display: flex;
        grid-gap: .5rem;
        margin-left: auto;
    }
    li {
        position: relative;
        border: var(--border);
        border-radius: 100%;
        list-style: none;
        
        transition: all .2s;
        cursor: pointer;
        height: 4rem;
        width: 4rem;
    }
    li:hover {
        transform: scale(1.1);
    }
    img {
        height: 50%;
        width: 50%;
    }

    @media only screen and (max-width: 650px) {
        ul {
            position: absolute;
            bottom: 1;
            right: 50%;
            transform: translateX(50%);
            flex-direction: column;
            justify-items: center;
            margin-top: 1rem;
        }
    }
    
</style>