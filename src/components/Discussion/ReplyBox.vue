<template>
  <div class="comment-tree-node pt-2 ml-14">
    <div class="comment-container items-center">
      <div class="avatar-container bg-white">
        <img
          class="avatar"
          src="../../assets/images/MansourFarabi.jpg"
          alt="may avatar"
        />
      </div>
      <div class="comment pt-0.5 ml-4 w-full pr-2">
        <CustomInput class="" placeholder="reply" type="text" />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import CustomInput from "../shared/form/CustomInput.vue";
</script>

<style lang="scss">
@import "../../assets/styles/discussion/reply-box.scss";
</style>
