<script>

    import Section from '../Section.svelte';
    import SkillTile from '../SkillTile.svelte';
    import * as skillsData from '../../data/skills.json';

    export let loading;
    export let handleOutroEnd;
    
    export let h;

    const aboutSum = "I am a passionate web developer who spends my freetime learning the latest technologies and sharing my passion with other like minded developers. I have experience in freelance and corperate development and always provide elegant, efficent results."

    let proficent = [];
    let comfortable = [];
    let learning = [];
    
    skillsData.default.forEach(skill => {
        if (skill.level == 3) proficent.push(skill)
        else if (skill.level == 2) comfortable.push(skill)
        else if (skill.level == 1) learning.push(skill)
    });

</script>

{#if !loading}
    <Section {h} {handleOutroEnd} sectionTitle="About Me">
        <div
            id="about_wrapper"
        >
            <div
                id="about_sum"
            >
                <div
                    id="headshot"
                >
                </div>
                <p>{aboutSum}</p>
            </div>
            <div
                id="skills"
            >
                <h2>Skills</h2>
                <ul>
                    {#each proficent as skill}
                        <SkillTile tech={skill.skill} />
                    {/each}
                </ul>
                <ul>
                    {#each comfortable as skill}
                        <SkillTile tech={skill.skill} />
                    {/each}
                </ul>
                <ul>
                    {#each learning as skill}
                        <SkillTile tech={skill.skill} />
                    {/each}
                </ul>
            </div>
        </div>
    </Section>
{/if}

<style>

    #about_wrapper {
        position: relative;
        height: 100%;
        width: 100%;
        padding: 1rem;
        display: grid;
        gap: 5vw;
    }

    #about_sum {
        display: grid;
        grid-template-columns: auto 1fr;
        gap: 3rem;
        place-items: center;
    }

    p {
        color: var(--color-white); 
        font-size: var(--font-size-p);
    }

    #headshot {
        height: 15vw;
        width: 15vw;
        min-width: 10rem;
        min-height: 10rem;
        background-color: var(--color-primary);
        border-radius: 100%;
    }

    h2 {
        font-size: var(--font-size-h3);
        color: var(--color-primary);
    }

    #skills {
        display: flex;
        flex-direction: column;
        gap: 3rem;
    }

    ul {
        width: 100%;
        list-style: none;
        display: flex;
        justify-content: center;
        gap: 1rem;
    }


    @media only screen and (max-width: 600px) {
        #about_sum {
            grid-template-columns: 100%;
        }

        #headshot {
            display: none;
        }
    }
</style>