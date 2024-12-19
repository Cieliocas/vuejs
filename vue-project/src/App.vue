<script setup>
const nome = "cielio castro";
const meuObj = {
	nome: "cielio",
	filmeFavorito: "matrix"
}

function dizOla() {
	return `${nome} diz oi`;
}
</script>

<template>
	<h1>{{ dizOla() }}</h1>
</template>

<style scoped>

</style>
