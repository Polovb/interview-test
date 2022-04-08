<template>
	<div>
		<!-- The list rendering now doesn't trigger the generation of the numbers list. -->
		<div class="number" :id="'number-'+number" :class="divisors.includes(number) ? 'active' : ''" v-for="number in numbers" :key="number" @mouseover="hov(number)" @mouseout="reset">
			{{number}}
		</div>
	</div>
</template>

<script>
export default {
	// Now using props instead of this.$parent so it's clearer in App.vue 
	props: ['limit'],
	
	// this is how the numbers list is generated now, which makes for cleaner logic and separation of concerns.
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
			// numbers is now the list used for rendering
			numbers: [],

			// this is generated on hover and emptied on mouseOut. Again, cleaner logic
			divisors: [],
		}
	},
	methods: {
		// this is practially identical except that it changes state instead of returning 
		numbersList()
		{
			let numbers = [];
			for(var i = 0; i < this.limit; i++) numbers = [...numbers, i];
			this.numbers = numbers.sort(() => Math.random() - 0.5);
		},
		
		// this is much cleaner as it doesn't need to go through the DOM, just the numbers state variable
		hov(number)
		{
			for(let i = 0; i < this.numbers.length; i++) if(number % i === 0) this.divisors = [...this.divisors, i];
		},

		// same here, it just needs to edit the state variable.
		reset()
		{
			this.divisors = [];
		}
	}
}
</script>


<style scoped>

/* I also made some minor style changes for aesthetics */

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
