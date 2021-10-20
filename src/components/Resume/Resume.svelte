<script>

    import * as skillsData from '../../data/skills.json';
    import * as experienceData from '../../data/experience.json';
    import * as courseData from '../../data/courses.json'
    
    import Section from '../Comps/Section.svelte';

    import ExperienceList from './ExperienceList.svelte';
    import Skills from './Skills.svelte';
    import Courses from './Courses.svelte';

    export let loading;
    export let handleOutroEnd;
    
    export let h;

</script>

{#if !loading}
    <Section {h} {loading} {handleOutroEnd} sectionTitle="Resume">
        <div
            id="resume_wrapper"
        >
            <Courses {courseData} />
            <Skills {skillsData} />
            <ExperienceList {experienceData} />
        </div>
    </Section>
{/if}

<style>

    #resume_wrapper {
        position: relative;
        height: 100%;
        width: 100%;
        display: grid;
        gap: 2rem;
        grid-template-columns: repeat(2, 1fr);
        padding: .5rem;
        align-items: center;
    }

    @media only screen and (max-width: 1100px) {
        #resume_wrapper {
            grid-template-columns: 1fr;
        }
    }

</style>