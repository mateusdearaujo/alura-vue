<template>
	<h2>{{ titulo }}</h2>
</template>

<script>
export default {
	name: "Painel",
	props: ['titulo']
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
</style>
