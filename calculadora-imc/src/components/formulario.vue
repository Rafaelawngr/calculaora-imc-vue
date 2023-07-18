<template>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
	<form>
		<fieldset>
			<label for="name">Nome completo</label>
			<input type="text" id="name" v-model="nome" name="name">
			<label for="height">Altura</label>
			<input type="number" id="height" v-model="altura" name="height">
			<label for="weight">Peso</label>
			<input type="number" id="weight" v-model="peso" name="weight">

			<div class="btn">
				<button @click="$emit('calcularImc')" class="btn-calculate">
					Calcular
				</button>
				<button @click="onclose()" class="btn-clean">
					Limpar
				</button>
			</div>
		</fieldset>
	</form>
</template>

<script>
import { ref } from 'vue'

export default {
	setup() {
		const nome = ref("");
		const altura = ref("");
		const peso = ref("");

		const calcularImc = (e) => {
			e.preventDefault()
			
			const alturaNum = Number(altura.value);
			const pesoNum = Number(peso.value)

			if (!isNaN(alturaNum) && !isNaN(pesoNum)) {
			let valorImc = (pesoNum / alturaNum ** 2).toFixed(2);
	console.log(nome.value, valorImc)
			} else {
				alert("Altura e peso devem ser números válidos.");
			}
		}

		
		return {
			nome,
			altura,
			peso,
			calcularImc
		};
	}
}
</script>


<style scoped>

fieldset {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
	gap: 20px;
	border: none;
}

label {
	font-size: 1rem;
	font-weight: 400;
	line-height: normal;
}

input {
	width: 326px;
	height: 50px;
	border-radius: 10px;
	border: none;
	background-color: #1D1D1D;
	padding: 20px;
	font-size: .80rem;
}

input:focus {
	outline: none;
}

.btn {
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 20px;
}

.btn-calculate {
	margin-top: 80px;
	display: flex;
	width: 326px;
	padding: 15px 0px;
	justify-content: center;
	align-items: center;
	gap: 10px;
	border: none;
	color: #ECECEC;
	font-size: 1rem;
	text-transform: uppercase;
	font-weight: 500;
	line-height: normal;
	border-radius: 10px;
	background: var(--botoes);
	cursor: pointer;
}

.btn-calculate:hover {
	transform: scale(1.05);
	transition: 200ms linear;
}

.btn-clean {
	font-size: 1rem;
	font-weight: 400;
	border: none;
	cursor: pointer;
}

.btn-clean:hover {
	color: var(--botoes);
	transform: scale(1.05);
	transition: 200ms linear;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
	-webkit-appearance: none;
	margin: 0;
}
</style>