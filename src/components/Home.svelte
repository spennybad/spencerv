<script>

    import Section from './Section.svelte';

    export let loading;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loading}
    <Section {h} {handleOutroEnd} sectionTitle="Home" styling="home">
        <div id="home_wrapper">
            <div id="photo">
                <img src="/images/channel-icon.jpeg" alt="French Boy"/>
            </div>
            <div id="home_text">
                <p><span>Hello!</span></p>
                <p>My name is Spencer and I am a web developer.</p>
                <p>I love staying up to date with the most modern tech and sharing my love for web development with others.</p>
            </div>
        </div>
    </Section>
{/if}

<style>
    
    #home_wrapper {
        display: grid;
        grid-template-rows: min-content auto;
        grid-template-columns: 40%;
        grid-gap: 2rem;
        justify-content: center;
    }

    #home_text > :not(:last-child) {
        margin-bottom: 1rem;
        justify-self: center;
    }

    p {
        color: var(--color-white);
        font-size: var(--font-size-p);
        text-align: center;
    }

    p span {
        color: var(--color-primary);
        font-size: calc(var(--font-size-p) + .5rem);
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

    @media only screen and (max-width: 1499px) {
        #home_wrapper {
            grid-template-columns: 50%;
        }
    }
    
    @media only screen and (max-width: 1100px) {
        #home_wrapper {
            grid-template-columns: 60%;
        }
    }
    
    @media only screen and (max-width: 800px) {
        #home_wrapper {
            grid-template-columns: 80%;
        }
    }

    @media only screen and (max-width: 800px) {
        #photo {
            height: 13rem;
            width: 13rem;
        }
    }

    @media only screen and (max-width: 600px) {
        #photo {
            height: 11rem;
            width: 11rem;
        }
    }

</style>