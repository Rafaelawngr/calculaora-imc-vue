<template>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Unica+One&display=swap" rel="stylesheet">
	<header class="title">
		{{ titulo }}
	</header>
</template>

<script>

import {ref, watch} from "vue";

export default {
	name: 'TitleComponent',
	props: {
		nome: {
			type: String,
			required: true
		}
	},
	
	setup(props) {
		
		let titulo = ref("calculadora de imc")
		
		watch(() => props.nome, () => {
			titulo.value = `${props.nome}, Seu IMC é:`;
		})
		
		return {
			titulo
		}
	}
}

</script>

<style scoped>

.title {
	display: flex;
	width: 326px;
	justify-content: center;
	align-items: center;
	font-family: Unica One,serif;
	font-size: 2rem;
	font-weight: 400;
	margin-top: 60px;
	margin-bottom: 80px;
}

</style>