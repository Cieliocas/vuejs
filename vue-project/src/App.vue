<script setup>
const nome = "cielio castro";
const meuObj = {
	nome: "cielio",
	filmeFavorito: "matrix"
}

function dizOla(nome) {
	return `${nome} diz: Olá!`;
}

const imagemJake ="https://i.pinimg.com/originals/de/64/c9/de64c999f00c57beccdaa5e70577eeef.png";
const imagemFinn = "https://static.wikia.nocookie.net/adventuretimewithfinnandjake/images/f/f3/Original_Finn.png";

const botaoEstaDesabilitado = false;

const gostaDoJake = false;
const gostaDoFinn = false;

const estaAutorizado = true;
</script>

<template>
	<h1>{{ dizOla("Jake") }}</h1>

	<img v-if="gostaDoJake" :src="imagemJake" alt="">
	<img v-else-if="gostaDoFinn" :src="imagemFinn" alt="">
	<h2 v-else>Não curte Hora de Aventura...</h2>

	<h1 v-if="estaAutorizado">Bem-vindo</h1>
	<h1 v-else>Não possui acesso</h1>

	<button :disabled="botaoEstaDesabilitado">Enviar mensagem</button>
</template>

<style scoped>

img {
	max-width: 200px;
}
</style>
