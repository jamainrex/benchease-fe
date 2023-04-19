<!-- eslint-disable vue/no-deprecated-html-element-is -->
<template>
  <ol class="step-indicator">
    <li
      v-for="step in steps"
      is="StepNavigationStep"
      :key="step.id"
      :step="step"
      :currentstep="currentstep"
    ></li>
  </ol>
</template>
<script>
import StepNavigationStep from "@/components/wizard/StepNavigationStep.vue"; // @ is an alias to /src
export default {
  name: "step-navigation",
  components: {
    StepNavigationStep,
  },
  props: ["steps", "currentstep"],
};
</script>
