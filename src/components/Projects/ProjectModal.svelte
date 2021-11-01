<script>
    import { fly } from 'svelte/transition';
    import SkillTile from '../Comps/SkillTile.svelte';

    export let clickedProject = undefined;
    export let handleOutroReset;

    let w;

    $: currentId = clickedProject ? clickedProject.id : currentId;

    const handleModalClose = () => {
        clickedProject = null;
        handleOutroReset();
    }

</script>

<svelte:window on:keydown={(event) => {if (clickedProject && event.code == "Escape") handleModalClose()}} />

{#if clickedProject}
    <div 
        bind:clientWidth={w}
        transition:fly="{{x: w, duration: 200}}"
        on:click|self={handleModalClose} 
        id="project_modal" 
        class="centeredInContainer"
    >
        <button 
            on:click={handleModalClose}
            id="exit_button"
        >
            <img
                src={"/images/x.svg"}
                alt={"Exit Icon."}
            >
        </button>

        <div id="project_modal_content">
            <div id="project_image_wrapper">
                <div id="project_links">
                    <a href={clickedProject.git} target="_blank" rel="noopener noreferrer"><p>See the Code</p><img src={"/images/github1.svg"} alt="github logo" /></a>
                    <a href={clickedProject.url} target="_blank" rel="noopener noreferrer"><p>Visit the Site</p><img src={"/images/earth.svg"} alt="internet/earth symbol" /></a>
                </div>
                <img
                    src={clickedProject.imagePath}
                    alt={clickedProject.desc}
                    id="project_image"
                >
            </div>
            <div id="project_modal_text">
                <p>{clickedProject.desc}</p>
                <ul>
                    {#each clickedProject.stackList as skill}
                        <SkillTile isResume={false} {skill}/>
                    {/each}
                </ul>
            </div>
        </div>
    </div>
{/if}

<style>
    #project_modal {
        height: 100%;
        width: 100%;
        
        position: fixed;
        z-index: 101;

        background-color: var(--color-black-trans90);
        box-shadow: var(--box-shadow-light);

        display: grid;
        place-items: center;

        grid-template-rows: auto 1fr;
    }

    #exit_button {
        margin: 1rem;
        border: none;
        background-color: transparent;
        appearance: none;

        height: 2rem;
        width: 2rem;

        font-size: var(--font-size-p);
        border-radius: 100%;
        cursor: pointer;
        filter: invert();
        transition: all .2s;
        justify-self: end;
    }

    #exit_button:hover {
        transform: scale(0.90);
    }

    #project_modal_content {
        display: grid;
        position: relative;
        padding-inline: 5vw;
        gap: 1rem;

        grid-template-columns: repeat(2, 1fr);
    }

    #project_image_wrapper {
        position: relative;
        overflow: hidden;
    }

    #project_links {
        position: absolute;
        bottom: 0;
        
        display: flex;
        flex-direction: column;

        gap: .5rem;
        margin-bottom: 1rem;
    }

    #project_links a {
        display: flex;
        justify-content: end;
        align-items: center;
        gap:1rem;
        padding: .5rem;
        background-color: var(--color-white);
        box-shadow: var(--box-shadow-primary);
        transform: translateX(calc(-100% + 3rem));
        transition: all .2s;
        text-decoration: none;
    }

    #project_links a p {
        font-size: var(--font-size-p);
        color: var(--color-black);
    }

    
    #project_links a:hover {
        transform: translateX(0rem);
    }

    #project_links a img {
        height: 2rem;
        width: 2rem;
    }


    #project_image {
        width: 100%;
        justify-self: end;
        align-self: center;
        border: 2px solid var(--color-white);
    }

    #project_modal_text {
        display: flex;
        flex-direction: column;
        align-self: center;
    }

    #project_modal_text ul {
        display: flex;
        width: 100%;
        flex-wrap: wrap;
        gap: 1rem;
        padding: 1rem;
    }

    #project_modal_text p {
        color: var(--color-white);
        background-color: var(--color-black-trans90);
        
        padding: 1rem;
        font-size: var(--font-size-p);
        width: 100%;
    }

    @media only screen and (max-width: 1100px) {
        
        #project_modal_content {
            grid-template-columns: 1fr;
        }

        #project_modal_text {
            text-align: center;
        }

        #project_modal_text ul {
            justify-content: center
        }

        #project_links a {
            transform: translateX(calc(-100% + 2.5rem));
        }

        #project_links a img {
            height: 1.5rem;
            width: 1.5rem;
        }
    }
    
</style>
 
