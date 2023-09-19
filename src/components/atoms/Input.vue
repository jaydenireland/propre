<script setup lang="ts">
import { ref, watch } from 'vue';

const { modelValue, required, label } = defineProps(['modelValue', 'required', 'label']);
const emit = defineEmits(['update:modelValue']);

const uuid = Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
const value = ref(modelValue);
watch(
	() => modelValue,
	(newVal) => {
		value.value = newVal;
	}
);

const updateValue = (event: Event) => {
	const newValue = (event.target as HTMLInputElement).value;
	value.value = newValue;
	emit('update:modelValue', newValue);
};
</script>

<template>
	<div class="my-2 flex items-center gap-4">
		<label class="font-bold" :for="uuid" v-if="label">
			{{ label }}
			<template v-if="required">
				<span class="text-red-500">*</span>
			</template>
		</label>
		<div class="input-wrapper relative">
			<input
				:id="uuid"
				:value="value"
				@input="(event) => updateValue(event)"
				type="text"
				class="input w-full p-2 !outline-none border-transparent focus:ring-0"
				v-bind="$attrs"
			/>

			<div class="border-animation z-10 bg-blue-500 h-[2px] w-0 absolute bottom-0 left-0 transition-all duration-500"></div>
			<div class="bg-black h-[1px] z-0 w-full absolute bottom-0 left-0"></div>
		</div>
	</div>
</template>

<style scoped>
.input:focus + .border-animation {
	width: 100%;
}
</style>
