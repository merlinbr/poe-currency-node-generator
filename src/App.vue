<template>
	<div id="app">
		<h1>Poe Currency Node Generator</h1>
		<CurrencyForm/>
	</div>
</template>

<script>
	import CurrencyForm from './components/CurrencyForm.vue'

	export default {
		name: 'app',
		components: {
			CurrencyForm
		}
	}
</script>

<style>
	body {
		background-color: #273646;
	}

	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: white;
		margin-top: 60px;
	}
</style>
