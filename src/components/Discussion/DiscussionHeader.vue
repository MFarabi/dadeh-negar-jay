<template>
  <header
    class="absolute top-0 left-0 w-full z-10 flex flex-row px-2 py-3 bg-white"
  >
    <img
      src="../../assets/images/MansourFarabi.jpg"
      alt="my avatar"
      class="avatar"
    />
    <CustomInput placeholder="Start a discussion" type="text" />
  </header>
</template>

<script lang="ts" setup>
import CustomInput from "../shared/form/CustomInput.vue";
</script>

<style lang="scss">
@import "../../assets/styles/discussion/discussion.scss";
</style>
