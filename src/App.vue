<script setup>
import { ref } from "vue";
import InputCustom from "./components/InputCustom.vue";
import ButtonSlot from "./components/ButtonSlot.vue";
const value = ref("1234");

function updateValueInput(param) {
	value.value = param;
}

const title = ref("Hello World");
</script>

<template>
	<ButtonSlot>
		<template #body="props">
			<template v-for="(item,index) in props.data" :key="index">
				<!-- <p>{{ item }}</p> -->
				<a>{{ item.title }}</a>
				<p>{{ item.content }}</p>
			</template>
		</template>
	</ButtonSlot>
</template>
<style scoped>
h3 {
	color: red;
}
</style>
