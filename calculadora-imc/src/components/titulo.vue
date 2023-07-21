<template>

	<header class="title">
		{{ $props.titulo }}
	</header>
</template>

<script>

export default {
	name: 'TitleComponent',
	props: {
    titulo: {
      type: String,
      required: true,
    }
	},
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
	margin-top: 25px;
	margin-bottom: 50px;
  text-align: center;
}

</style>