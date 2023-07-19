<template>
	<div>
		<TitleComponent :nome="nome"></TitleComponent>
		<FormComponent @resultado-calculado="showResults"></FormComponent>
		<ResultsComponent :valor-imc="valorImc"></ResultsComponent>
		
	</div>
</template>

<script>

import { ref } from "vue";
import TitleComponent from "@/components/titulo.vue";
import FormComponent from "@/components/formulario.vue";
import ResultsComponent from "@/components/resultado.vue";

export default {
	name: 'App',
	components: {
		ResultsComponent,
		FormComponent,
		TitleComponent,
	},
	
	setup() {
	
		const nome = ref("");
		const valorImc = ref(0);
		
		const showResults = (imc) => {
			valorImc.value = imc
		}
		
		
		return {
			nome,
			valorImc,
			showResults
		};

	}
}
</script>



