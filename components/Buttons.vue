<template>
  <div class="text-sm mt-2 flex items-center">
    <transition name="fade">
      <span class="opacity-0" v-show="appear">保存しました</span>
    </transition>
    <button
      class="px-4 py-1 border border-black rounded-sm bg-gray-100 hover:bg-gray-200 active:bg-gray-300 ml-auto"
      @click="clearText"
    >
      削除
    </button>
    <button
      class="px-4 py-1 border border-black ml-1 rounded-sm bg-gray-100 hover:bg-gray-200 active:bg-gray-300"
      @click="saveText"
    >
      保存
    </button>
  </div>
</template>
<script setup>
const props = defineProps(["appear"]);
const emit = defineEmits(["saveText", "clearText"]);
const saveText = () => {
  emit("saveText");
};
const clearText = () => {
  emit("clearText");
};
</script>
