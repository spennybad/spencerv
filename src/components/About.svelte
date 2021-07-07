<script>

    import Section from './Section.svelte';

    export let loaded;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loaded}
    <Section {h} {handleOutroEnd} sectionTitle="About Me">
        <div id="about_wrapper">
            <div id="photo">
                <img src="/images/channel-icon.jpeg" alt="French Boy"/>
            </div>
            <div id="about_text">
                <p><span>Hello!</span></p>
                <p>My name is Spencer and I am a web developer.</p>
                <p>I love staying up to date with the most modern tech and sharing my love for web development with others.</p>
            </div>
        </div>
    </Section>
{/if}

<style>
    
    #about_wrapper {
        display: grid;
        grid-template-rows: min-content auto;
        grid-gap: 2rem;
    }

    #about_text > :not(:last-child) {
        margin-bottom: 1rem;
        justify-self: center;
    }

    p {
        color: var(--color-white);
        font-size: var(--font-size-p);
        background-color: var(--color-black-trans75);
        text-align: center;
    }

    p span {
        color: var(--color-primary);
        font-size: calc(var(--font-size-p) + 1rem);
    }

    #photo {
        background-color: var(--color-white);
        border-radius: 100%;
        height: 15rem;
        width: 15rem;
        position: relative;
        overflow: hidden;
        border: 1px solid var(--color-white);
        justify-self: center; /* In loving memory of "P_G_" <3 */
    }

    #photo img {
        height: 100%;
        width: 100%;
        object-fit: cover;
    }

</style>