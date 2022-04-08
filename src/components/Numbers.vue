<script setup>
import {ref, watch, onMounted} from 'vue';

onMounted(()=>numbersList());
watch(()=>props.limit, ()=>numbersList());

const props = defineProps(['limit']);

const numbers = ref([]);
const divisors = ref([]);

function numbersList()
{
	let nums = [];
	for(var i = 0; i < props.limit; i++) nums = [...nums, i];
	numbers.value = nums.sort(() => Math.random() - 0.5);
}

function hov(number)
{
	for(let i = 0; i < numbers.value.length; i++) if(number % i === 0) divisors.value = [...divisors.value, i];
}

function reset()
{
	divisors.value = [];
}

</script>

<template>
	<div>
		<!-- <div class="number" :class="isActive(number) ? 'active' : ''" v-for="number in numbers" :key="number" @mouseover="hov(number)" @mouseout="reset"> -->
		<div class="number" :class="divisors.includes(number) ? 'active' : ''" v-for="number in numbers" :key="number" @mouseover="hov(number)" @mouseout="reset">
			{{number}}
		</div>
	</div>
</template>


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
