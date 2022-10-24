<script setup>
import { ref } from 'vue'
import IconFlatGame from './components/icons/IconFlatGame.vue'
import axios from 'axios'
const info = ref([])

const getAdvice = () => {
	axios
		.get('https://api.adviceslip.com/advice')
		.then(res => (info.value = res.data))
}
getAdvice()
</script>

<template>
	<div class="parent">
		<div v-if="info != ''" class="advice">
			<p class="advice__id">Advice #{{ info.slip.id }}</p>
			<h1 class="advice__advice">"{{ info.slip.advice }}"</h1>
		</div>
		<div class="line">
			<div class="l-1"></div>
			<div class="l-2">
				<div></div>
				<div></div>
			</div>
			<div class="l-3"></div>
		</div>
		<div>
			<button class="flatBtn" @click="getAdvice"><IconFlatGame /></button>
		</div>
	</div>
</template>

<style scoped></style>
