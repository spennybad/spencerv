<script>

    import Section from '../Comps/Section.svelte';
    import SkillTile from '../Comps/SkillTile.svelte';
    import * as skillsData from '../../data/skills.json';

    export let loading;
    export let handleOutroEnd;
    
    export let h;
    
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
    <Section {h} {loading} {handleOutroEnd} sectionTitle="Resume">
        <div
            id="resume_wrapper"
        >
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

    #resume_wrapper {
        position: relative;
        height: 100%;
        width: 100%;
        display: grid;
        gap: 5vw;
    }

    h2 {
        font-size: var(--font-size-h3);
        color: var(--color-primary);
    }

    #skills {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    ul {
        width: 100%;
        list-style: none;
        display: flex;
        justify-content: center;
        gap: 1rem;
    }

</style>