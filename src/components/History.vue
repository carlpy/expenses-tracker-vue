<script setup>

const props = defineProps({
	transactionsInfo: {
		type: Array,
		required: true
	},
})

</script>

<template>
	<div class="mb-6"> <!-- History.vue -->
		<p class="text-xl font-medium">History</p>
		<hr class="my-3">

		<ul>
			<li class="group relative flex justify-between bg-white border-1 border-gray-200 rounded-tl-sm rounded-bl-sm shadow-sm mb-3 py-1.5 px-4"
				v-for="(transaction, index) in transactionsInfo" :key="index">
				<span class="absolute -left-1 w-1 h-full top-0"
					:class="transaction.amount < 0 ? 'bg-rose-600' : 'bg-green-400'"></span>
				<p>{{ transaction.title }}</p>
				<span>${{ transaction.amount }}</span>

				<button @click="transactionsInfo.splice(index, 1)"
					class="hidden bg-rose-600 text-white absolute p-3 py-2.5 -right-[39px] top-0 rounded-tr-md rounded-br-md group-hover:flex items-center justify-center">
					<span class="icon-[mdi--delete]" role="img" aria-hidden="true" />
				</button>
			</li>

		</ul>
	</div>
</template>