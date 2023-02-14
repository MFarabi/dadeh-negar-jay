<template>
  <!-- center -->
  <div
    class="flex justify-center items-center overflow-y-scroll overflow-hidden"
    :class="isMobile ? [] : []"
  >
    <!-- mobile -->
    <div class="sm:shrink-0 md:w-96 lg:w-96">
      <div class="pt-20 p-3 pr-5 relative" :class="isMobile ? [] : ['border']">
        <DiscussionHeader />
        <Discussion :discussions="discussions" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { provide } from "vue";
import Discussion from "./components/Discussion/Discussion.vue";
import DiscussionHeader from "./components/Discussion/DiscussionHeader.vue";
import discussions from "./Mock/discussion";

const isMobile =
  /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
    navigator.userAgent
  );

provide("isMobile", isMobile);
</script>
