<script setup>
import Avatar from "./Avatar.vue";
import { ref } from "vue";
import { defineProps, defineEmits,provide } from "vue";
const props = defineProps({
	cardProp: Object,
});
provide('hello', listCard);

const hehehe = defineEmits(["closePopup", "saveCard","deleteCard"]);
const cardPropCopy = ref(props.cardProp);
const isFetching = ref(true);
function fethData() {
	setTimeout(() => {
		isFetching.value = false;
	}, 100);
}
fethData();
function save() {
	hehehe("saveCard", { id: "id-123", title: "Card 1", description: "Description 1" });
}
function deleteCard() {
	hehehe("deleteCard");
}
</script>

<template>
	<div v-if="isFetching">
		<p>Loading...</p>
	</div>
	<div v-else class="container">
		<h1 class="heading-1">Card Detail</h1>
		<div :class="card">
			<div class="card__image">
				<img src="https://via.placeholder.com/150" alt="Card Image" />
			</div>
			<div class="card__content">
				<h2 class="heading-2">{{ cardProp.title }}</h2>
				<p class="paragraph">{{ cardProp.description }}</p>
			</div>
		</div>
		<button @click="$emit('closePopup')">Cancel</button>
		<button @click="save">Save</button>
		<button @click="deleteCard">Delete</button>
	</div>

</template>

<style scoped>
.container {
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: 20px;
	border-radius: 10px;
	border: 1px solid #ccc;
}
.heading-1 {
	color: blue;
}

.card {
	display: flex;
	border: 1px solid #ccc;
	border-radius: 5px;
	margin: 10px;
	padding: 10px;
}

.card__image {
	margin-right: 10px;
}

.card__content {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}

.heading-2 {
	font-size: 1.5rem;
	margin: 0;
}

.paragraph {
	margin: 0;
}
</style>
