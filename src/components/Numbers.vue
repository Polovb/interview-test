<template>
	<div>
		<div class="number" :class="isActive(number) ? 'active' : ''" v-for="number in numbers" :key="number" @mouseover="hov(number)" @mouseout="reset">
			{{number}}
		</div>
	</div>
</template>

<script>
export default {
	props: ['limit'],
	beforeMount(){
		this.numbersList();
	},
	watch:{
		limit: function(){
			this.numbersList();
		},
	},
	data()
	{
		return {
			numbers: [],
			divisors: [],
		}
	},
	methods: {
		numbersList()
		{
			let numbers = [];
			for(var i = 0; i < this.limit; i++) numbers = [...numbers, i];
			this.numbers = numbers.sort(() => Math.random() - 0.5);
		},
		hov(number)
		{
			for(let i = 0; i < this.numbers.length; i++) if(number % i === 0) this.divisors = [...this.divisors, i];
		},
		isActive(number){
			return this.divisors.includes(number);
		},
		reset()
		{
			this.divisors = [];
		}
	}
}
</script>

<style scoped>
	.number {
		display: inline-block;
		padding: 3px 5px;
		background-color: hsl(0, 0%, 93%);
		margin: 5px;
		border-radius: 3px;
		border: 1px solid hsl(0, 0%, 0%, 0.1);
		/* box-shadow: 1px 1px 0px 1px hsl(0,0%,0%, 0.1); */
		font-family: Arial, Helvetica, sans-serif;
		cursor: default;
	}

	.active {
		background-color: red;
		color: white;
		border-color: hsl(0, 0%, 0%, 0.4);
	}
</style>
