<script setup>
const nome = "cielio castro";
const meuObj = {
	nome: "cielio",
	filmeFavorito: "matrix"
}

function dizOla(nome) {
	return `${nome} diz: Olá!`;
}

const endDaImagemJake ="https://i.pinimg.com/originals/de/64/c9/de64c999f00c57beccdaa5e70577eeef.png";
const botaoEstaDesabilitado = false;
</script>

<template>
	<h1>{{ dizOla("Jake") }}</h1>
	<img :src="endDaImagemJake" alt="">

	<button :disabled="botaoEstaDesabilitado">Enviar mensagem</button>
</template>

<style scoped>

</style>
