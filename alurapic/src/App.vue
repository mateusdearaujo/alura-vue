<template>
<div class="container">
	<h1>{{ title }}</h1>
	<label>
		<input v-on:input="filtro = $event.target.value" type="text" class="filtro" placeholder="Busque pelo titulo">
	</label>
	<div class="content" >
		<div v-for="foto of fotosComFiltro" class="images-content">
			<Painel :titulo="foto.titulo" :url="foto.url"/>
		</div>
	</div>
</div>
</template>

<script>
import Painel from './components/Painel';

export default {
	components: {Painel},
	data() {
		return {
			title: 'Projeto Alura Pic',
			fotos: [],
			filtro: ''
		}
	},
	created() {
		this.$http.get('http://localhost:3000/v1/fotos')
			.then(response => response.json())
			.then(fotos => this.fotos = fotos)
			.catch(err => console.log(err))
	},
	computed: {
		fotosComFiltro() {
			if(this.filtro) {
				let exp = new RegExp(this.filtro.trim(), 'i')
				return this.fotos.filter(foto => exp.test(foto.titulo))
			} else {
				return this.fotos;
			}
		}
	}
}
</script>

<style>
body {
	margin: 0;
}

.container {
	max-width: 100vw;
	display: block;
	text-align: center;
	font-family: Helvetica, sans-serif;
}

.content {
	display: flex;
	flex-wrap: wrap;
	margin: 0 auto;
	justify-content: center;
}

.images-content {
	width: 50%;
	padding: 10px;
	box-sizing: border-box;
	margin-bottom: 10px;
}

.filtro {
	display: block;
	width: 40%;
	margin: 0 auto;
}

</style>
