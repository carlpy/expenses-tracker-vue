<script setup>
import { ref } from 'vue';

import TransactionResult from './TransactionResult.vue';
import History from './History.vue';
import AddNewTransaction from './AddNewTransaction.vue';


const transactions = ref([
	{ title: 'The book of the five rings', amount: 50 },
	{ title: 'PS5', amount: -250 },
	{ title: 'Black album Collection Edition', amount: 15 },
	{ title: 'Assassin\'s Creed Mirage', amount: -50 },
	{ title: 'Vue Course', amount: 300 },
	{ title: 'Benelli Leoncino 250', amount: 3000 }
]);

function AddTransaction([title, amount]) {
	transactions.value.push({
		title,
		amount
	})
}
</script>

<template>
	<main class="min-h-screen grid place-content-center bg-slate-100">
		<section class="max-w-sm p-8">
			<TransactionResult :transactionsInfo="transactions"></TransactionResult>

			<History :transactions-info="transactions"></History>

			<AddNewTransaction @add-new-transaction="AddTransaction"></AddNewTransaction>
		</section>
	</main>
</template>