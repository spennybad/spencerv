<script>
    import SkillList from './SkillList.svelte';

    export let skillsData;

    let proficent = [];
    let comfortable = [];
    let learning = [];
    
    skillsData.default.forEach(skill => {
        if (skill.level == 3) proficent.push(skill)
        else if (skill.level == 2) comfortable.push(skill)
        else if (skill.level == 1) learning.push(skill)
    });

</script>

<ul id="skills">
  <h3>Skills</h3>
  <SkillList skills={proficent} level={"proficent"} />
  <SkillList skills={comfortable} level={"comfortable"} />
  <SkillList skills={learning} level={"learning"} />
</ul>

<style>

    
</style>
