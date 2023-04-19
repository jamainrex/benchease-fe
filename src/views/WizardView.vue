<template>
  <div class="wizard">
    <StepNavigation :steps="steps" :currentstep="currentstep"> </StepNavigation>

    <div v-show="currentstep == 1">
      <h3>Step 1 - Get Started</h3>
      <div class="voice-content">Welcome to Benchease</div>
      <div class="form-group">
        <label for="email">Email address</label>
        <input
          type="email"
          name="email"
          class="form-control"
          aria-describedby="emailHelp"
          placeholder="Enter email"
        />
        <small id="emailHelp" class="form-text text-muted"
          >We'll never share your email with anyone else.</small
        >
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input
          type="password"
          name="password"
          class="form-control"
          placeholder="Password"
        />
      </div>
    </div>

    <div v-show="currentstep == 2">
      <h3>Step 2</h3>
      <div class="form-group">
        <label for="select">Example select</label>
        <select class="form-control" name="select">
          <option>1</option>
          <option>2</option>
          <option>3</option>
          <option>4</option>
          <option>5</option>
        </select>
      </div>
    </div>

    <div v-show="currentstep == 3">
      <h3>Step 3</h3>
      <div class="form-group">
        <label for="textarea">Example textarea</label>
        <textarea class="form-control" name="textarea" rows="4"></textarea>
      </div>
      <div class="form-group">
        <label for="file">File input</label>
        <input
          type="file"
          class="form-control-file"
          name="file"
          aria-describedby="fileHelp"
        />
        <small id="fileHelp" class="form-text text-muted"
          >This is some placeholder block-level help text for the above input.
          It's a bit lighter and easily wraps to a new line.</small
        >
      </div>
    </div>

    <Step
      v-for="step in steps"
      :currentstep="currentstep"
      :key="step.id"
      :step="step"
      :stepcount="steps.length"
      @step-change="stepChanged"
    >
    </Step>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StepNavigation from "@/components/wizard/StepNavigation.vue"; // @ is an alias to /src
import Step from "@/components/wizard/Step.vue"; // @ is an alias to /src

export default defineComponent({
  name: "WizardView",
  components: {
    StepNavigation,
    Step,
  },
  data: function () {
    return {
      currentstep: 1,

      steps: [
        {
          id: 1,
          title: "Personal",
          icon_class: "fa fa-user-circle-o",
        },
        {
          id: 2,
          title: "Details",
          icon_class: "fa fa-th-list",
        },
        {
          id: 3,
          title: "Send",
          icon_class: "fa fa-paper-plane",
        },
      ],
    };
  },

  methods: {
    stepChanged(step: number) {
      this.currentstep = step;
    },
  },
});
</script>
<style lang="scss">
@import "../assets/wizard.scss";
</style>
