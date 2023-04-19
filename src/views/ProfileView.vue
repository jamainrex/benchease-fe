<template>
  <div class="container profile">
    <ProfileHeader />
    <ProfileDetails />
    <ProfileSkills />
  </div>
</template>

<script lang="ts">
import ProfileHeader from "@/components/ProfileHeader.vue";
import ProfileDetails from "@/components/ProfileDetails.vue";
import ProfileSkills from "@/components/ProfileSkills.vue";

import { defineComponent } from "vue";

export default defineComponent({
  name: "ProfileView",
  components: {
    ProfileDetails,
    ProfileHeader,
    ProfileSkills,
  },
  props: {
    msg: String,
  },
});
</script>
