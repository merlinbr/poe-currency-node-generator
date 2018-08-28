<template>
	<el-main>
		<el-row :gutter="20" align="center">
			<el-col class="grid-content">
				<h2 class="sub-title">Currency that you want to sell</h2>
			</el-col>
		</el-row>
		<el-row>
			<el-select v-model="emptySellValue" filterable placeholder="Select" class="currency-select">
				<el-option
						v-for="item in options"
						:key="item.value"
						:label="item.label"
						:value="item.value">
				</el-option>
			</el-select>
			<el-input placeholder="Amount" type="number" v-model="sellAmount" class="currency-Amount"></el-input>
		</el-row>
		<el-row :gutter="20" align="center">
			<el-col class="grid-content">
				<h2 class="sub-title">Currency that you want to buy</h2>
			</el-col>
		</el-row>
		<el-row>
			<el-select v-model="emptyBuyValue" filterable placeholder="Select" class="currency-select">
				<el-option
						v-for="item in options"
						:key="item.value"
						:label="item.label"
						:value="item.value">
				</el-option>
			</el-select>
			<el-input placeholder="Amount" type="number" v-model="buyAmount" class="currency-Amount"></el-input>
		</el-row>
	</el-main>
</template>

<script>
	export default {
		name: 'CurrencyForm',
		data() {
			return {
				options: [{
					value: 'Option1',
					label: 'Chaos Orb'
				}, {
					value: 'Option2',
					label: 'Exalted Orb'
				}, {
					value: 'Option3',
					label: 'Chromatic Orb'
				}, {
					value: 'Option4',
					label: 'Alchemy Orb'
				}, {
					value: 'Option5',
					label: 'Orb of Fusing'
				}],
				emptyValue: ''
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.currency-select {
		width: 17em;
	}
	.currency-Amount {
		width: 10em;
		margin-left: 1em;
		margin-top: 1em;
	}
	.sub-title {
		margin: 0.8em 0 0 0;
	}
</style>
