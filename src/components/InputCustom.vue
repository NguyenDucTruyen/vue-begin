<script setup>
import {defineModel, defineProps } from "vue";

const vmModelCustom = defineModel('hehe');
const vModelTitle = defineModel('title');
function changeTitle() {
    vModelTitle.value = "title mới";
}

</script>

<template>
	<div>
		<button @click="changeTitle">Change Title</button>
		<br />
		<input v-model="vmModelCustom" />
		<br />
        <textarea name="" id=""></textarea>
	</div>
</template>
