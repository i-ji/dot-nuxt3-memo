<template>
  <div>
    <textarea
      class="w-full box-border h-40 border border-black rounded-sm p-2 mt-2"
      v-model="text"
    ></textarea>
    <Buttons @saveText="saveText" @clearText="clearText" :appear="appear" />
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";
const text = ref("");
const appear = ref(false);

onMounted(() => {
  if (localStorage.getItem("memo") === null) {
    text.value = "";
  } else {
    text.value = localStorage.getItem("memo");
  }
});

const saveText = () => {
  if (text.value === "") return;
  localStorage.setItem("memo", text.value);
  appear.value = true;
  setTimeout(() => {
    appear.value = false;
  }, 5000);
};

const clearText = () => {
  if (confirm("本当に削除しますか?")) {
    localStorage.removeItem("memo");
    text.value = "";
  }
};
</script>
