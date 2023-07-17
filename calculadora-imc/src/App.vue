<template>
  <titulo
  />
	<formulario />
</template>

<script>
import titulo from './components/titulo.vue'
import formulario from './components/formulario.vue'

export default {
	name: 'App',
	components: {
		titulo,
		formulario
	},
	// setup () {
	// 	const calcularIMC = () => {
	//		
	// 	}
	// }
}
</script>



