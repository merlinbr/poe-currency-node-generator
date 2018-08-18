<template>
	<div id="app">
		<el-container>
			<el-header>
				<h2>Poe Currency Node Generator</h2>
			</el-header>
			<el-main>
				<CurrencyForm></CurrencyForm>
			</el-main>
		</el-container>
	</div>
</template>

<script>
	import CurrencyForm from './components/CurrencyForm.vue'

	export default {
		data() {
			return {}
		},
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
