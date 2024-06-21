<script setup>
import { ref } from 'vue';

const newTransactionTitle = ref('');
const newTransactionAmount = ref('');

const emits = defineEmits(['addNewTransaction']);

function AddTransaction() {
	emits('addNewTransaction', [newTransactionTitle.value, newTransactionAmount.value])

	newTransactionTitle.value = '';
	newTransactionAmount.value = '';
}



</script>

<template>
	<div> <!-- AddNewTransaction.vue -->
		<p class="text-xl font-medium">Add new transaction</p>
		<hr class="my-3">

		<form @submit.prevent="AddTransaction">
			<div class="mb-4">
				<p class="mb-1 text-sm font-medium">Text</p>
				<input v-model="newTransactionTitle" class="border border-1 border-gray-300 rounded py-1 px-3 w-full"
					type="text" placeholder="Enter text...">
			</div>
			<div class="mb-4">
				<p class="mb-1 text-sm font-medium">Amount (Negative-Expense Positive-Income)</p>
				<input v-model="newTransactionAmount"
					class="hide-arrow border border-1 border-gray-300 rounded py-1 px-3 w-full" type="number"
					placeholder="Enter amount...">
			</div>
			<button type="submit" class="bg-purple-500 text-white px-4 py-2 text-center w-full rounded">Add
				transaction</button>
		</form>
	</div>
</template>
