<template>
	<div>
    
		<TitleComponent :titulo="tituloPagina"></TitleComponent>
    <div v-show="showFirstPage">
		<FormComponent @resultado-calculado="showResults"></FormComponent>
    </div>
    <div v-show="showSecondPage">
		<ResultsComponent :valorimc="valorImc" @go-back="onGoBack"></ResultsComponent>
    </div>
	</div>
</template>

<script>

import { ref } from "vue";
import TitleComponent from "@/components/titulo.vue";
import FormComponent from "@/components/formulario.vue";
import ResultsComponent from "@/components/resultado.vue"

export default {
	name: 'App',
	components: {
		ResultsComponent,
		FormComponent,
		TitleComponent,
	},
	
	setup() {
	
    const tituloPagina = ref("Calculadora de IMC")
		const valorImc = ref(0);
    let showFirstPage = ref (true)
    let showSecondPage = ref (false)
		
		const showResults = (imc, nome) => {
			valorImc.value = imc
      showFirstPage.value = false;
      showSecondPage.value = true;
      tituloPagina.value = `${nome}, Seu IMC é:`;
		}
    
    const onGoBack = () => {
      showFirstPage.value = true;
      showSecondPage.value = false;
      tituloPagina.value = `Calculadora de IMC`;
    }
    
		
		return {
			valorImc,
      showFirstPage,
      showSecondPage,
      tituloPagina,
			showResults,
      onGoBack
		};

	}
}
</script>



