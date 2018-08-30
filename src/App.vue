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

	export default {
		data() {
			return {
				formData: null
			}
		},
		mounted() {
			this.initializeEventBus();
		},
		name: 'app',
		components: {
			CurrencyForm
		},
		methods: {
			initializeEventBus() {
				// Listen for the get-form-data event and its payload (formData).
				EventBus.$on('get-form-data', formValues => {
					if (formValues) {
						this.formData = formValues;
						this.generateCurrencyNode();
					}
				});
			},
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
		width: 27em;
		margin-left: auto;
		margin-right: auto;
	}
</style>
