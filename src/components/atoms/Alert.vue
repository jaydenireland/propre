<script setup lang="ts">
const { status } = withDefaults(
	defineProps<{
		status: 'primary' | 'success' | 'warning' | 'danger' | 'neutral';
	}>(),
	{
		status: 'primary'
	}
);
const classes = [
	status === 'primary' ? 'bg-propre-blue-700 text-white' : '',
	status === 'success' ? 'bg-propre-green-700 text-white' : '',
	status === 'warning' ? 'bg-propre-yellow-400 text-black' : '',
	status === 'danger' ? 'bg-propre-red-700 text-white' : '',
	status === 'neutral' ? 'bg-propre-gray-700 text-white' : ''
];
</script>

<template>
	<div :class="classes" class="h-2 m-2 p-4 flex items-center justify-center">
		<p class="ml-auto">
			<slot></slot>
		</p>
		<div class="ml-auto">x</div>
	</div>
</template>
