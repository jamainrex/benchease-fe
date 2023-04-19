<template>
  <section class="card shadow">
    <img class="card-img" src="../assets/user.png" alt="user" />
    <div class="theme-bg-color card-header text-white">
      <h1>John Doe</h1>
      <p>UI/UX Designer</p>
    </div>
    <div class="card-body">
      <div class="container">
        <div class="row align-items-start">
          <div class="col">
            <img src="../assets/location.png" alt="user" />
            <span>Hybrid</span>
          </div>
          <div class="col">
            <img src="../assets/time.png" alt="user" />
            <span>7:00AM - 4:00PM </span>
          </div>
          <div class="col">
            <img src="../assets/mail.png" alt="user" />
            <span>johnd@codev.com</span>
          </div>
        </div>
        <div class="row align-items-center">
          <div class="col">
            <img src="../assets/people.png" alt="user" />
            <span>Codev Talent Mgmt.</span>
          </div>
          <div class="col">
            <img src="../assets/calendar.png" alt="user" />
            <span>Tuesday - Saturday</span>
          </div>
          <div class="col">
            <img src="../assets/phone.png" alt="user" />
            <span>09123456789</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ProfileDetails",
});
</script>
<style lang="scss">
.card-img {
  position: absolute;
  left: 90px;
  z-index: 1;
  top: 60px;
  max-width: 157px;
}
.card-header {
  padding-left: 300px !important;
  padding-top: 54px !important;
  padding-bottom: 4px !important;
  height: 136px;
  text-align: left;
}
.card-body {
  padding-left: 320px !important;
  margin: 31px 0;
  text-align: left;

  .col {
    margin-bottom: 21px;
  }

  img {
    padding-right: 15px;
  }
}
</style>
