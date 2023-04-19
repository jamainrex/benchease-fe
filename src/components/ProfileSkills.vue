<template>
  <div class="container profile-skills">
    <div class="text-end btn-container">
      <button
        type="button"
        class="btn btn-primary theme-bg-color theme-border-color"
      >
        <img src="../assets/plus.png" alt="plus" />
        Add Skill
      </button>
    </div>

    <div class="row">
      <div>
        <h3 class="text-start">Primary Skills</h3>
      </div>
      <div class="d-inline-flex">
        <button
          v-for="(skill, i) in skills.primary"
          type="button"
          class="btn btn-primary theme-bg-color theme-border-color mr-3"
          :key="i"
        >
          {{ skill }}
        </button>
      </div>
    </div>
    <div class="row">
      <div>
        <h3 class="text-start">Additional Skills</h3>
      </div>
      <div class="d-inline-flex">
        <button
          v-for="(skill, i) in skills.additional"
          type="button"
          class="btn btn-primary"
          :key="i"
        >
          {{ skill }}
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ProfileSkills",
  data() {
    return {
      skills: {
        primary: [
          "Javascript",
          "ReactJS",
          "PHP Development",
          "WordPress Development ",
          "UI Design",
        ],
        additional: [
          "Quality Assurance",
          "Automation Testing",
          "HTML/CSS",
          "Product Design",
          "SEO Content",
          "UI/UX",
          "Google Analytics",
          "Selenium",
        ],
      },
    };
  },
});
</script>
<style lang="scss">
.profile-skills {
  margin-top: 29px;

  .btn-container + .row {
    margin-bottom: 65px;
  }
  h3 {
    font-size: 18px;
    line-height: 27px;
  }
  .btn {
    margin-right: 16px;
  }
}
</style>
