<script setup>
import { reactive } from 'vue';

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

const gostaDoJake = true;
const gostaDoFinn = false;

const estaAutorizado = true;

// let contador = 0;
const estado = reactive({
	contador: 0,
	email: '',
	saldo: 5000,
	transferindo: 0,
	nomes: ['Gian', 'Cielio', 'Paulo', 'Luisa'],
	nomeAInserir: '',
});

function incrementar() {
	estado.contador++;
}

function decrementar() {
	estado.contador--;
}

function alteraEmail(event) {
	estado.email = event.target.value;
}

function saldoFuturo() {
	const { saldo, transferindo } = estado;
	return saldo - transferindo;
}

function validaValor() {
	const { saldo, transferindo} = estado;
	return saldo >= transferindo;
}

function cadastraNome() {
	if (!estado.nomeAInserir.length >= 3) {
		estado.nomes.push(estado.nomeAInserir)
	} else {
		alert("Digite mais de 3 caracteres");
	}
}

</script>

<template>
	<h1>{{ dizOla("Jake") }}</h1>

	<img v-if="gostaDoJake" :src="imagemJake" alt="">
	<img v-else-if="gostaDoFinn" :src="imagemFinn" alt="">
	<h2 v-else>Não curte Hora de Aventura...</h2>

	<h1 v-if="estaAutorizado">Bem-vindo</h1>
	<h1 v-else>Não possui acesso</h1>

	<button :disabled="botaoEstaDesabilitado">Enviar mensagem</button>

	<br />
	<hr />

	{{ estado.contador }}
	<button @click="incrementar" type="button">+</button>
	<button @click="decrementar" type="button">-</button>
	
	<br />
	<hr />

	{{ estado.email }}
	<input type="email" @change="alteraEmail" placeholder="Digite seu email" />

	<br />
	<hr />

	Saldo: {{ estado.saldo }} <br />
	Transferindo: {{ estado.transferindo }} <br />
	Saldo depois da transferência: {{ saldoFuturo() }} <br />
	<input class="campo" :class="{ invalido: !validaValor() }" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir" />
	<button v-if="validaValor()">Transferir</button>
	<span v-else>Valor maior que o saldo</span>

	<br />
	<hr />

	<ul>
		<li v-for="nome in estado.nomes">
			{{ nome }}
		</li>
	</ul>
	<input @keyup="evento => estado.nomeAInserir = evento.target.value" type="text" placeholder="Digite um nome">
	<button @click="cadastraNome" type="button">Cadastrar nome</button>

</template>

<style scoped>

img {
	max-width: 200px;
}

.invalido {
	outline-color: red;
	border-color: red;
}

.campo {
	border: 2px solid #4c00ff;
}
</style>
