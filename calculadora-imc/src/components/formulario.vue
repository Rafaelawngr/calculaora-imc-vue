<template>
	<form @submit.prevent="calcularImc">
		<fieldset>
			<label for="name">Nome</label>
			<input type="text" id="name" v-model="nome" name="name" autocomplete="off">
			<label for="height">Altura</label>
			<input type="number" step="0.01" id="height" v-model.number="altura" name="height">
			<label for="weight">Peso</label>
			<input type="number" id="weight" v-model.number="peso" name="weight">

			<div class="btn">
				<button class="btn-calculate">
					Calcular
				</button>
				<button type="button" class="btn-clean" @click="cleanData">
					Limpar
				</button>
			</div>
		</fieldset>
	</form>

</template>

<script>
import {ref} from 'vue'

export default {
	name: 'FormComponent',
	emits: [
		'resultado-calculado',
    'historico-imc'
	],

  props: {
    
    },
    
	setup(_, {emit}) {
		const nome = ref("");
		const altura = ref(null);
		const peso = ref(null);
    const usersArray = ref([]);
		
		const calcularImc = () => {
    let valorImc;

			if (!isNaN(altura.value) && !isNaN(peso.value) && altura.value !== 0 && peso.value !== 0 && altura.value !== null && peso.value !== null ) {
				valorImc = peso.value / altura.value ** 2;
				emit("resultado-calculado", valorImc, nome.value);
			
			} else {
				alert("Altura e peso devem ser números válidos.");
			}
     
      usersArray.value.push({
        id: Date.now(),
        nome: nome.value,
        altura: altura.value,
        peso: peso.value,
        imc: valorImc.toFixed(1)
      })
        emit("historico-imc", usersArray.value);
		}
    
		const cleanData = () => {
			nome.value = "";
			altura.value = "";
			peso.value = "";
		}
		
		return {
			nome,
			altura,
			peso,
			calcularImc,
			cleanData,
      usersArray
		};
	}
}
</script>


<style scoped>

fieldset {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
	gap: 15px;
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
	margin-top: 30px;
	display: flex;
	width: 326px;
	padding: 15px 0;
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