<script setup lang="ts">
import { computed } from 'vue';

const classes = ['p-2', 'rounded'];
const { status, disabled, variant } = withDefaults(
	defineProps<{
		status: 'primary' | 'success' | 'warning' | 'danger' | 'neutral';
		disabled: boolean;
		variant: 'solid' | 'outline';
	}>(),
	{
		status: 'primary',
		disabled: false,
		variant: 'solid'
	}
);

// type for statuses
type Statuses = {
	primary: {
		solid: string;
		outline: string;
	};
	success: {
		solid: string;
		outline: string;
	};
	warning: {
		solid: string;
		outline: string;
	};
	danger: {
		solid: string;
		outline: string;
	};
	neutral: {
		solid: string;
		outline: string;
	};
};

const statuses: Statuses = {
	primary: {
		solid: 'bg-propre-blue-700 text-white',
		outline: 'border-propre-blue-700 text-propre-blue-700'
	},
	success: {
		solid: 'bg-propre-green-700 text-white',
		outline: 'border-propre-green-700 text-propre-green-700'
	},
	warning: {
		solid: 'bg-propre-yellow-400 text-black',
		outline: 'border-propre-yellow-400'
	},
	danger: {
		solid: 'bg-propre-red-700 text-white',
		outline: 'border-propre-red-700 text-propre-red-700'
	},
	neutral: {
		solid: 'bg-propre-gray-700 text-white',
		outline: 'border-propre-gray-700 text-propre-gray-700'
	}
};

const classList = computed(() => {
	return [
		...classes,
		statuses[status][variant],
		disabled ? 'opacity-40 cursor-not-allowed pointer-events-none' : '',
		!disabled && variant === 'solid' ? 'hover:brightness-75' : '',
		!disabled && variant === 'outline' ? 'bg-transparent border-2' : ''
	];
});
</script>

<template>
	<button :class="classList">
		<slot></slot>
	</button>
</template>
