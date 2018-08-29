<template>
	<div id="app">
		<el-container>
			<el-header>
				<h2>Poe Currency Node Generator</h2>
			</el-header>
			<CurrencyForm></CurrencyForm>
		</el-container>
	</div>
</template>

<script>
	import CurrencyForm from './components/CurrencyForm.vue'
	import { EventBus } from './event-bus.js'

	// Listen for the get-form-data event and its payload (formData).
	EventBus.$on('get-form-data', formData => {
		this.formData = formData;
	});

	export default {
		data() {
			return {
				formData: null
			}
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
		margin-top: 30px;
	}
</style>
