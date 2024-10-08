<script setup>
import { defineEmits,defineProps,inject } from "vue";
const list = inject("hello");
defineProps(["imgLink"]);
const emit = defineEmits(["updateAvatar"]);
function updateAvatar() {
    console.log("updateAvatar");
    emit("updateAvatar");
}
</script>
<template>
	<div class="avatar" @click="updateAvatar">
		<span>Link:{{ list }}</span>
        
	</div>
</template>
