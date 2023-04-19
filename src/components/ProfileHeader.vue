<template>
  <div class="container profile-header">
    <div class="row">
      <div class="col-6">
        <h3 class="theme-color-text text-start">SKILLS</h3>
      </div>
      <div class="col-6">
        <div class="profile-header-details d-flex justify-content-end">
          <img src="../assets/user.png" alt="..." width="51" height="51" />
          <div>
            <h6>John Doe</h6>
            <p>UI/UX Designer</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ProfileHeader",
});
</script>
<style lang="scss">
.profile-header {
  h3 {
    font-size: 35px;
    line-height: 52px;
  }
  .profile-header-details {
    padding-left: 12px;

    h6 {
      font-size: 18px;
      line-height: 27px;
    }
    p {
      font-size: 10px;
      line-height: 15px;
    }
  }
}
</style>
