<script setup>

import { computed } from 'vue';

const props = defineProps({
	transactionsInfo: Array,
});

const transactionOp = computed(() => {
	return {
		balance: props.transactionsInfo.reduce((prev, curr) => {
			prev += curr.amount; return prev;
		}, 0),

		income: props.transactionsInfo.reduce((prev, curr) => {
			if (curr.amount > 0) {
				prev += curr.amount;
			}
			return prev;
		}, 0),
		expenses: props.transactionsInfo.reduce((prev, curr) => {
			if (curr.amount < 0) {
				prev -= curr.amount;
			}
			return prev;
		}, 0),
	};
});
</script>

<template>
	<h1 class="text-2xl font-semibold mb-4">Expenses Tracker</h1>

	<div class="mb-5">
		<h2 class="text-sm font-medium">YOUR BALANCE</h2>
		<span class="font-semibold text-2xl">${{ transactionOp.balance }}</span>
	</div>

	<div
		class="flex items-center justify-center bg-white divide-x-2 mb-5 p-3.5 rounded border-1 border-gray-200 shadow-md">

		<div class="pr-8 text-center">
			<p class="font-medium">INCOME</p>
			<span class="text-lg font-medium text-green-400">${{ transactionOp.income }}</span>
		</div>
		<div class="pl-8 text-center">
			<p class="font-medium">EXPENSES</p>
			<span class="text-lg font-medium text-rose-600">-${{ transactionOp.expenses }}</span>
		</div>
	</div>
</template>