<template>
<div class="container">
	<h1>{{ title }}</h1>
	<div class="content" >
		<div v-for="foto of fotos" class="images-content">
			<h2>{{ foto.titulo }}</h2>
			<img :src='foto.url' :title='foto.titulo' :alt='foto.titulo' class='images'>
		</div>
	</div>
</div>
</template>

<script>
export default {
	data() {
		return {
			title: 'Projeto Alura Pic',
			fotos: []
		}
	},
	created() {
		this.$http.get('http://localhost:3000/v1/fotos')
			.then(response => response.json())
			.then(fotos => this.fotos = fotos)
			.catch(err => console.log(err))
		console.log(this.fotos)
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
	width: 25%;
	padding: 10px;
	box-sizing: border-box;
	margin-bottom: 10px;
}
.images-content h2 {
	background: #3498db;
	margin-bottom: 0;
	height: 50px;
	display: flex;
	align-items: center;
	justify-content: center;
	border: 5px solid #000;
}

.images {
	width: 100%;
	height: 280px;
	-webkit-box-shadow: 10px 10px 29px -5px rgba(0,0,0,0.75);
	-moz-box-shadow: 10px 10px 29px -5px rgba(0,0,0,0.75);
	box-shadow: 10px 10px 29px -5px rgba(0,0,0,0.75);
}
</style>
