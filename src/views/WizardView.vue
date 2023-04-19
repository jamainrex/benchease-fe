<!-- eslint-disable vue/require-v-for-key -->
<template>
  <div class="wizard">
    <div class="form-group" v-if="voiceList.length">
      <label for="voices">Select a voice</label>
      <select class="form-control" id="voices" v-model="selectedVoice">
        <option
          v-for="(voice, index) in voiceList"
          :data-lang="voice.lang"
          :value="index"
        >
          {{ voice.name }} ({{ voice.lang }})
        </option>
      </select>
    </div>
    <StepNavigation :steps="steps" :currentstep="currentstep"> </StepNavigation>

    <div v-show="currentstep == 1">
      <h3>Step 1 - Get Started</h3>
      <div class="voice-content-1" ref="content1">Welcome to Benchease</div>
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
      <div class="voice-content-2">
        As a bench team member, you'll have a chance to enhance your skills,
        retool your expertise, and prepare for future client engagements with
        confidence.
      </div>
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
      <div class="voice-content-3">Step 3 Text voice</div>
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

    <div v-show="currentstep == 4">
      <h3>Completed!</h3>
      <div class="voice-content-4">
        Thank you for completing your Profile Information.
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

<script>
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
        {
          id: 4,
          title: "Completed",
          icon_class: "fa fa-check",
        },
      ],
      isLoading: true,
      selectedVoice: 0,
      synth: window.speechSynthesis,
      voiceList: [],
      greetingSpeech: new window.SpeechSynthesisUtterance(),
      textToSpeech: [
        "Welcome to Benchease",
        "As a bench team member, you'll have a chance to enhance your skills, retool your expertise, and prepare for future client engagements with confidence.",
      ],
    };
  },

  async mounted() {
    // wait for voices to load
    // I can't get FF to work without calling this first
    // Chrome works on the onvoiceschanged function
    this.voiceList = await this.synth.getVoices();
    //console.log(this.voiceList);

    if (this.voiceList.length) {
      this.isLoading = false;
      //this.speak("Hello World!");
    }

    this.synth.onvoiceschanged = async () => {
      this.voiceList = await this.synth.getVoices();
      // give a bit of delay to show loading screen
      // just for the sake of it, I suppose. Not the best reason
      setTimeout(() => {
        this.isLoading = false;
        //this.speak("Hello World!");
      }, 800);
    };

    this.listenForSpeechEvents();
    //console.log(this.currentstep);
    //this.speak("Hello World!");
    this.$nextTick(() => {
      setTimeout(() => {
        console.log(this.voiceList);
        //this.isLoading = false;
        //this.speak("Hello World!");
        this.getTextToSpeech(this.currentstep);
      }, 3000);
    });
  },

  methods: {
    stepChanged(step) {
      this.currentstep = step;
      this.getTextToSpeech(this.currentstep);
    },
    listenForSpeechEvents() {
      this.greetingSpeech.onstart = () => {
        this.isLoading = true;
      };

      this.greetingSpeech.onend = () => {
        this.isLoading = false;
      };
    },
    getTextToSpeech(step) {
      console.log(this.textToSpeech[step - 1]);
      this.speak(this.textToSpeech[step - 1]);
    },
    /**
     * Shout at the user
     */
    speak(text) {
      console.log(text, this.synth, this.greetingSpeech, this.voiceList);
      // it should be 'craic', but it doesn't sound right
      this.greetingSpeech.text = text;

      this.greetingSpeech.voice = this.voiceList[this.selectedVoice];

      this.synth.speak(this.greetingSpeech);
    },
  },
  // these vuejs function will simple run when the web- application loads
  // generally like $(document).ready in jQuery like as a vuejs
  created() {
    //console.log("OnReady!");
    //this.getTextToSpeech(this.currentstep);
  },
});
</script>
<style lang="scss">
@import "../assets/wizard.scss";
</style>
