<template>
  <input
    :placeholder="placeholder"
    :type="type"
    class="border border-gray-300 outline-0 focus:border-gray-300 py-2.5 px-3 rounded text-gray-500 text-sm tracking-wide w-full mx-5"
  />
</template>

<script lang="ts" setup>
const { type } = withDefaults(
  defineProps<{ type: string; placeholder: string }>(),
  {
    type: "text",
    placeholder: "",
  }
);
</script>
