<template>
	<div id="app">
		<el-container>
			<el-header>
				<h2>Poe Currency Note Generator</h2>
			</el-header>
			<CurrencyForm></CurrencyForm>
			<el-row :gutter="20" v-if="formData">
				<el-col align="center" class="grid-content" :span="14" :offset="5">
					Press to copy <br>
					<el-button id="note-btn" @click="copyToClipboard">
						{{ note }}
					</el-button>
					<br> (Select "Note" on "{{ this.formData.sellValueLabel }}" in your stash and paste the created note)
				</el-col>
			</el-row>
		</el-container>
	</div>
</template>

<script>
	import CurrencyForm from './components/CurrencyForm.vue'
	import { EventBus } from './event-bus.js'

	export default {
		data() {
			return {
				formData: null,
				note: ''
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
						this.generateCurrencyNote();
					} else {
						this.formData = null;
					}
				});
			},
			generateCurrencyNote() {
				const buyAmount = this.formData.buyAmount;
				const sellAmount = this.formData.sellAmount;
				const buyCurrency = this.formData.buyValue;
				
				this.note = '~b/o ' + buyAmount + '/' + sellAmount + ' ' + buyCurrency;
				this.copyToClipboard();
				this.openClipboardSuccessNotification();
			},
			copyToClipboard() {
				/* Create placeholder textArea for the select function */
				let textArea = document.createElement("textarea");

				/* Set textArea value to the note */
				textArea.value = this.note;
				document.body.appendChild(textArea);

				/* Select the text field of the textArea */
				textArea.select();

				/* Copy the text from the text field */
				document.execCommand("Copy");

				/* Remove placeholder textArea */
				textArea.remove();

				this.openClipboardSuccessNotification();
			},
			openClipboardSuccessNotification() {
				this.$message({
					message: 'Copied to clipboard.',
					type: 'success'
				});
			}
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
		margin-top: 10px;
		width: 27em;
		margin-left: auto;
		margin-right: auto;
	}

	#note-btn {
		margin-top: 5px;
		margin-bottom: 5px;
	}
</style>
