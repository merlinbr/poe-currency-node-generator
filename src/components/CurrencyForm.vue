<template>
	<el-container>
		<el-select v-model="emptyValue" filterable placeholder="Select">
			<el-option
					v-for="item in options"
					:key="item.value"
					:label="item.label"
					:value="item.value">
			</el-option>
		</el-select>
	</el-container>
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
</style>
