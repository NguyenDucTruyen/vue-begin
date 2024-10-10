<script setup>
import { defineEmits,defineProps,inject, defineOptions } from "vue";
defineOptions({
  inheritAttrs: true
})
const list = inject("hello");
defineProps(["imgLink"]);
const emit = defineEmits(["updateAvatar"]);
function updateAvatar() {
    console.log("updateAvatar");
    emit("updateAvatar");
}
</script>
<template>
	<div @click="updateAvatar">
		<span>Link:{{ list }}</span>
	</div>
</template>
<style scoped>
.avatar {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    border-radius: 10px;
    border: 1px solid #ccc;
    gap: 10px;
    background-color: #ddd;
}
</style>
