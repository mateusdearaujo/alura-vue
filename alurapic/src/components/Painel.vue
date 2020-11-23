<template>
	<div>
		<h2 @click.self="visivel = !visivel">{{ titulo }}</h2>
		<transition name="painel-fade">
			<img :src='url' :title='titulo' :alt='titulo' class='images' v-show="visivel">
		</transition>
	</div>
</template>

<script>
export default {
	name: "Painel",
	props: ['titulo', 'url'],
	data() {
		return {
			visivel: true
		}
	}
}
</script>

<style scoped>
h2 {
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

.painel-fade-enter, .painel-fade-leave-active {
	opacity: 0;
}

.painel-fade-enter-active, .painel-fade-leave-active {
	transition: opacity .5s;
}

</style>
