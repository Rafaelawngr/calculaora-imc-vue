<template>
	<div>
    
		<TitleComponent :titulo="tituloPagina" />
    <div v-show="showFirstPage">
		<FormComponent  @historico-imc="mostrarHistorico" @resultado-calculado="showResults" />
    </div>
    <div v-show="showSecondPage">
		<ResultsComponent :valorimc="valorImc" @go-back="onGoBack" />
    </div>
    <HistoricoComponent :historico="usersArray"/>
	</div>
</template>

<script>

import { ref } from "vue";
import TitleComponent from "@/components/titulo.vue";
import FormComponent from "@/components/formulario.vue";
import ResultsComponent from "@/components/resultado.vue"
import HistoricoComponent from "./components/historico.vue";

export default {
	name: 'App',
	components: {
    HistoricoComponent,
		ResultsComponent,
		FormComponent,
		TitleComponent,
	},
	
	setup() {
	
    const tituloPagina = ref("Calculadora de IMC")
		const valorImc = ref(0);
    let showFirstPage = ref (true)
    let showSecondPage = ref (false)
    let usersArray = ref ([])
		
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
    
    const mostrarHistorico = (array) => {
      usersArray.value = array
    }
		
		return {
			valorImc,
      showFirstPage,
      showSecondPage,
      tituloPagina,
			showResults,
      onGoBack,
      mostrarHistorico,
      usersArray
		};

	}
}
</script>



