<template>
	<el-main>
		<el-form ref="form" :model="form">
			<el-form-item>
				<el-row :gutter="20" align="center">
					<el-col class="grid-content">
						<h2 class="sub-title">Currency that I want to buy</h2>
					</el-col>
				</el-row>
				<el-row>
					<el-select v-model="buyValue" filterable placeholder="Select" class="currency-select">
						<el-option
								v-for="item in form.options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
						</el-option>
					</el-select>
					<el-input placeholder="Amount" type="number" v-model="buyAmount" class="currency-Amount"></el-input>
				</el-row>
			</el-form-item>
			<el-form-item>
				<el-row :gutter="20" align="center">
					<el-col class="grid-content">
						<h2 class="sub-title">Currency that I want to sell</h2>
					</el-col>
				</el-row>
				<el-row>
					<el-select v-model="sellValue" filterable placeholder="Select" class="currency-select">
						<el-option
								v-for="item in form.options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
						</el-option>
					</el-select>
					<el-input placeholder="Amount" type="number" v-model="sellAmount" class="currency-Amount"></el-input>
				</el-row>
			</el-form-item>
			<el-form-item>
				<el-button type="primary" @click="emitGlobalSendFormEvent">Create Node</el-button>
				<el-button @click="resetForm">Reset</el-button>
			</el-form-item>
		</el-form>
	</el-main>
</template>

<script>
	import { EventBus } from '../event-bus.js'

	export default {
		name: 'CurrencyForm',
		methods: {
			emitGlobalSendFormEvent() {
				if ( this.allValuesSet() ) {
					const formValues = {
						sellValue: this.sellValue,
						sellAmount: this.sellAmount,
						buyValue: this.buyValue,
						buyAmount: this.buyAmount
					};

					this.resetForm();
					// Send the event on a channel (get-form-data) with a payload (the form data)
					EventBus.$emit('get-form-data', formValues);
				}
			},
			resetForm() {
				this.sellValue = null;
				this.sellAmount = null;
				this.buyValue = null;
				this.buyAmount = null
			},
			allValuesSet() {
				let allValuesSet = true;

				if (this.sellValue === null) {
					allValuesSet = false;
				}
				if (this.sellAmount === null) {
					allValuesSet = false;
				}
				if (this.buyValue === null) {
					allValuesSet = false;
				}
				if (this.buyAmount === null) {
					allValuesSet = false;
				}

				return allValuesSet;
			}
		},
		data() {
			return {
				sellValue: '',
				buyValue: '',
				sellAmount: '',
				buyAmount: '',
				form: {
					options: [{
						value: 'blesse',
						label: 'Blessed Orb'
					}, {
						value: 'chisel',
						label: 'Cartographer\'s Chisel'
					}, {
						value: 'chrom',
						label: 'Chromatic Orb'
					}, {
						value: 'chaos',
						label: 'Chaos Orb'
					}, {
						value: 'divine',
						label: 'Divine Orb'
					}, {
						value: 'exalted',
						label: 'Exalted Orb'
					}, {
						value: 'gcp',
						label: 'Gemcutter\'s Prism'
					}, {
						value: 'jew',
						label: 'Jeweller\'s Orb'
					}, {
						value: 'alchemy',
						label: 'Orb of Alchemy'
					}, {
						value: 'alt',
						label: 'Orb of Alteration'
					}, {
						value: 'chance',
						label: 'Orb of Chance'
					}, {
						value: 'fuse',
						label: 'Orb of Fusing'
					}, {
						value: 'regret',
						label: 'Orb of Regret'
					}, {
						value: 'scour',
						label: 'Orb of Scouring'
					}, {
						value: 'regal',
						label: 'Regal Orb'
					}, {
						value: 'vaal',
						label: 'Vaal Orb'
					}, {
						value: 'perandus',
						label: 'Perandus Coin'
					}, {
						value: 'silver',
						label: 'Silver Coin'
					}, {
						value: 'glass',
						label: 'Glassblower\'s Bauble'
					}, {
						value: 'aug',
						label: 'Orb of Augmentation'
					}, {
						value: 'mir',
						label: 'Mirror of Kalandra'
					}, {
						value: 'tra',
						label: 'Orb of Transmutation'
					}, {
						value: 'blacksmith',
						label: 'Blacksmith\'s Whetstone'
					}, {
						value: 'armour',
						label: 'Armourer\'s Scrap'
					}, {
						value: 'wis',
						label: 'Scroll of Wisdom'
					}, {
						value: 'port',
						label: 'Portal Scroll'
					}, {
						value: 'ete',
						label: 'Eternal Orb'
					}, {
						value: 'offer',
						label: 'Offering to the Goddess'
					}, {
						value: 'dusk',
						label: 'Sacrifice at Dusk'
					}, {
						value: 'midnight',
						label: 'Sacrifice at Midnight'
					}, {
						value: 'dawn',
						label: 'Sacrifice at Dawn'
					}, {
						value: 'noon',
						label: 'Sacrifice at Noon'
					}, {
						value: 'grie',
						label: 'Mortal Grief'
					}, {
						value: 'rage',
						label: 'Mortal Rage'
					}, {
						value: 'hope',
						label: 'Mortal Hope'
					}, {
						value: 'ign',
						label: 'Mortal Ignorance'
					}, {
						value: 'hydra',
						label: 'Fragment of the Hydra'
					}, {
						value: 'phoenix',
						label: 'Fragment of the Phoenix'
					}, {
						value: 'minot',
						label: 'Fragment of the Minotaur'
					}, {
						value: 'chimer',
						label: 'Fragment of the Chimera'
					}, {
						value: 'apprentice-sextant',
						label: 'Apprentice Cartographer\'s Sextant'
					}, {
						value: 'journeyman-sextant',
						label: 'Journeyman Cartographer\'s Sextant'
					}, {
						value: 'master-sextant',
						label: 'Master Cartographer\'s Sextant'
					}]
				}
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
