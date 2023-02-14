<template>
  <div
    class="comment-tree-node pt-3 ml-6"
    :class="{ 'reply-border': !isReply }"
  >
    <div class="comment-container ml-8">
      <div class="avatar-container" :class="{ 'bg-white': !isReply }">
        <img
          class="avatar"
          :src="discussion.user.avatar"
          :alt="discussion.user.name + 'avatar'"
        />
      </div>
      <div class="comment ml-1">
        <h5 class="mb-2 text-gray-700">
          {{ discussion.user.name }}
          <span class="text-gray-200 text-sm"
            >{{
              moment
                .duration(
                  moment(new Date(Date.now())).diff(moment(discussion.date))
                )
                .humanize()
            }}
            ago</span
          >
        </h5>
        <p
          class="text-justify text-gray-500 text-xs leading-5 tracking-tighter"
        >
          {{ discussion.text }}
        </p>
        <div class="text-sm flex mt-2">
          <button
            class="py-1 px-2 rounded-full text-white flex items-center justify-center w-14"
            :class="{
              'bg-blue-600': discussion.iLikedIt,
              'bg-gray-200': !discussion.iLikedIt,
            }"
          >
            <LikeSvgComponent
              class="w-3.5 mr-2"
              :color="discussion.iLikedIt ? 'white' : 'gray'"
            />
            <p
              class="text-xs mb-0"
              :class="{ 'text-gray-800': !discussion.iLikedIt }"
            >
              {{ discussion.likes }}
            </p>
          </button>
          <button
            v-if="!isReply"
            @click="showReply = !showReply"
            class="ml-5 text-blue-700"
          >
            Reply
          </button>
        </div>
      </div>
    </div>
    <CommentTreeNode
      v-for="reply in discussion.replies"
      :discussion="{ ...reply, replies: [] }"
      :is-reply="true"
      :class="{ 'py-5': isReply }"
      class="ml-14"
    />
    <ReplyBox v-if="!isReply" class="ml-12 mr-4" />
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import moment from "moment";
import ReplyBox from "./ReplyBox.vue";
import { IDiscussion } from "../../types/discussions";
import LikeSvgComponent from "./../shared/svg/LikeSvgComponent.vue";

const { discussion } = withDefaults(
  defineProps<{
    discussion: IDiscussion;
    isReply: boolean;
  }>(),
  { isReply: false }
);

const showReply = ref<boolean>(false);
</script>

<style lang="scss">
@import "../../assets/styles/discussion/comment-tree-node.scss";
</style>
