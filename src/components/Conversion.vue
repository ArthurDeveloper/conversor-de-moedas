<template>
	<div>
		<Coin :value="coins[0]" :name="from.split('/')[0]" v-on:valueChange="(value) => { coinValueChange(0, value); convert() }"/>
		<span>para</span>
		<Coin :value="coins[1]" :name="to.split('/')[0]" v-on:valueChange="(value) => { coinValueChange(1, value); convert() }"/>
	</div>
</template>

<script>
import Coin from './Coin';

export default {
	name: 'Conversion',
	props: {
		from: String,
		to: String
	},
	components: {
		Coin
	},
	data() {
		return {
			coins: [null, null],
			lastChangedCoin: 0
		}
	},
	methods: {
		coinValueChange(coinIndex, value) {
			this.lastChangedCoin = coinIndex;
			this.coins[coinIndex] = value;
			if (isNaN(Number(this.coins[coinIndex]))) {
				this.coins[coinIndex] = null;
			}
		},
		convert() {

			const coinCodes = [this.from.split('/')[1], this.to.split('/')[1]];

			fetch(`https://economia.awesomeapi.com.br/json/daily/${coinCodes[0]}-${coinCodes[1]}/`)
				.then((res) => {
					return res.json();
				}).then((data) => {
					if (this.lastChangedCoin == 0) {
						this.coins[1] = (this.coins[0]/data[0].high) || null;
					} else if (this.lastChangedCoin == 1) {
						this.coins[0] = (this.coins[1]*data[0].high) || null;
					}
				}).catch((err) => {
					console.error(err);
				});
		}
	}
}
</script>

<style scoped>
	div {
		display: flex;
		flex-direction: row;
		align-items: center;
		margin-left: 12px;
		margin-right: 12px;
		margin-top: 5px;
		margin-bottom: 5px;
	}
</style>