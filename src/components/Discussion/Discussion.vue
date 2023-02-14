<template>
  <div :class="!isMobile ? ['h-128', 'overflow-y-scroll'] : []">
    <CommentTreeNode
      v-for="discussion in discussions"
      :discussion="discussion"
      :is-reply="false"
    />
  </div>
</template>

<script lang="ts" setup>
import { inject } from "vue";
import { IDiscussion } from "../../types/discussions";
import CommentTreeNode from "./CommentTreeNode.vue";

defineProps<{ discussions: IDiscussion[] }>();

const isMobile: boolean = inject("isMobile")!;
</script>

<style lang="scss">
@import "./../../assets/styles/discussion/discussion.scss";
</style>
