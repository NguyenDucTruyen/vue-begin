<script setup>
import { ref, computed } from "vue";
const data = ref([
	{ title: "Chăn 1", content: "Content 1" },
	{ title: "ga 2", content: "Content 2" },
	{ title: "gối 3", content: "Content 3" },
]);
const page = ref(1);

const currentData = computed(() => {
    // fetch('https://jsonplaceholder.typicode.com/posts',{
    //     method: 'GET',
    //     params: {
    //         title: search.value,
    //         page: page.value
    //     }
    // })
    

	return data.value.filter((item) => item.title.includes(search.value)).slice(page.value - 1, page.value);
});
const search = ref("");
</script>

<template>
	<div>
		<h3>Table product</h3>
		<input v-model="search" placeholder="Search" type="text" />
        <br>

		<slot name="body" :data="currentData">Title</slot>

		<button @click="page = 1"><<</button>
		<button @click="page = 1">1</button>
		<button @click="page = 2">2</button>
		<button @click="page = data.length">>></button>
	</div>
</template>
<style scoped>
button {
	padding: 10px 20px;
	background-color: #007bff;
	color: white;
	border: none;
	border-radius: 5px;
	cursor: pointer;
}
</style>
