<script setup>
import { ref, provide } from "vue";
import CardDetail from "./components/CardDetail.vue";
import Avatar from "./components/Avatar.vue";
const listCard = ref([
	{
		id: 1,
		title: "Card 1",
		description: "Description 1",
	},
	{
		id: 2,
		title: "Card 2",
		description: "Description 2",
	},
	{
		id: 3,
		title: "Card 3",
		description: "Description 3",
	},
]);
const CardDetailVisible = ref(false);
function showDetail() {
	CardDetailVisible.value = true;
}
function closePopupDetail(...a) {
	CardDetailVisible.value = false;
	console.log(a);
}
function updateCard(value) {
	CardDetailVisible.value = false;
	const { id, ...body } = value;
	console.log(value);
	console.log(id);
	console.log(body);}
function updateAvatar() {
	console.log("updateAvatar tren App.vue");
}
</script>
<template>
	<div class="container">
		<li v-for="item in listCard" :key="item.id" @click="showDetail">
			<h2 class="heading-2">{{ item.title }}</h2>
			<p class="paragraph">{{ item.description }}</p>
		</li>
	</div>
	<CardDetail
		v-if="CardDetailVisible"
		:cardProp="listCard[0]"
		@updateAvatar="updateAvatar"
		:imgLink="'https://emduy.jpg'"
		@closePopup="closePopupDetail"
		@saveCard="updateCard"
	/>
	<Avatar/>
</template>
<style scoped>
.ahihi {
	color: red;
}
.container {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: 20px;
	border-radius: 10px;
	border: 1px solid #ccc;
	gap: 10px;
}
li {
	list-style-type: none;
	border: 1px solid #ccc;
	background-color: #ddd;
}
</style>
