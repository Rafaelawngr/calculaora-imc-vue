<template>
	<div>
	<titulo/>
	<formulario/>
	<resultado v-if="calcularImc"/>
	</div>
</template>

<script>

import Titulo from "@/components/titulo.vue";
import Formulario from "@/components/formulario.vue";
import Resultado from "@/components/resultado.vue";

export default {
	name: 'App',
	components: {
		Resultado,
		Formulario,
		Titulo

	},
	setup() {

		return {
			
		};

	}
}
</script>



