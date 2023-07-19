<template>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Trispace:wght@700&display=swap" rel="stylesheet">
	<link rel="stylesheet"
	      href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"/>
	<div class="content">
		<div class="result-borda">
			<div class="result">
				<div class="valor">
					{{ displayValorImc }}
				</div>
				<div class="classification-title">Classificação:
				</div>
				<div class="classification">
					{{ classificacaoImc }}
				</div>
			</div>
		</div>
		<div>
		</div>
		<button class="btn-voltar" @click="goBack"><span class="material-symbols-outlined">
arrow_back
</span>Voltar
		</button>
	</div>
</template>

<script>

import {ref, watch} from 'vue'
import TitleComponent from "@/components/titulo.vue";

export default {
	name:'ResultsComponent',
	
	props: {
		valorImc: Number
	},
	components: {
		TitleComponent
	},
	setup(props) {
		
		const goBack = () => {
			window.history.back()
		}

		let classificacaoImc = ref("");
		let displayValorImc = ref("")
		
		watch( () => props.valorImc, (novoValor, valorAntigo) => {
			if (novoValor !== valorAntigo) {
				if (props.valorImc < 18.5) {
					classificacaoImc.value = "Abaixo do peso";
				} else if (props.valorImc <= 25) {
					classificacaoImc.value = 'Peso normal';
				} else if (props.valorImc <= 30) {
					classificacaoImc.value = 'Sobrepeso';
				} else if (props.valorImc <= 35) {
					classificacaoImc.value = 'Obesidade grau I';
				} else if (props.valorImc <= 40) {
					classificacaoImc.value = 'Obesidade grau II';
				} else {
					classificacaoImc.value = 'Obesidade grau III';
				}

				displayValorImc.value = props.valorImc.toFixed(1)
			}
		
	});
		
		return {
			classificacaoImc,
			displayValorImc,
			goBack
		}
	}
}

</script>

<style scoped>
.content {
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 50px;
}

.result-borda {
	display: flex;
	align-items: center;
	justify-content: center;
	width: 340px;
	height: 340px;
	border-radius: 340px;
	background: #1D1D1D;
	position: relative;
}

.result {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	width: 300px;
	height: 300px;
	border-radius: 300px;
	background: var(--botoes);
	position: absolute;

}

.valor {
	font-family: 'Trispace', sans-serif;
	font-size: 80px;
	font-weight: 700;
	background-color: transparent;
	padding: 20px;
}

.classification-title {
	font-size: .80rem;
	font-weight: 400;
	background-color: transparent;
}

.classification {
	font-size: 1.2rem;
	font-weight: 500;
	background-color: transparent;
}

.btn-voltar {
	display: flex;
	font-size: 1rem;
	font-weight: 400;
	border: none;
	cursor: pointer;
	gap: 10px;
}

.btn-voltar:hover {
	color: var(--botoes);
	transform: scale(1.05);
	transition: 200ms linear;
}

.material-symbols-outlined {
	font-variation-settings: 'FILL' 0,
	'wght' 400,
	'GRAD' 0,
	'opsz' 16
}

</style>