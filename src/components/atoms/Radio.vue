<template>
	<div class="inline-flex items-center">
		<label class="relative flex cursor-pointer items-center rounded-full p-3">
			<input
				v-bind="$attrs"
				type="radio"
				@click="value = !value"
				class="before:content[''] peer border-black relative h-5 w-5 cursor-pointer appearance-none rounded-full border border-blue-gray-200 text-propre-blue-700 transition-all before:absolute before:top-2/4 before:left-2/4 before:block before:h-12 before:w-12 before:-translate-y-2/4 before:-translate-x-2/4 before:rounded-full before:bg-blue-gray-500 before:opacity-0 before:transition-opacity checked:border-propre-blue-700 checked:before:bg-propre-blue-700 hover:before:opacity-10"
				:checked="value"
			/>
			<div class="pointer-events-none absolute top-2/4 left-2/4 -translate-y-2/4 -translate-x-2/4 text-propre-blue-700 opacity-0 transition-opacity peer-checked:opacity-100">
				<svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 16 16" fill="currentColor">
					<circle data-name="ellipse" cx="8" cy="8" r="8"></circle>
				</svg>
			</div>
		</label>
	</div>
</template>
<script lang="ts">
export default {
	props: ['modelValue'],
	computed: {
		value: {
			get() {
				return this.modelValue;
			},
			set(value: boolean) {
				this.$emit('update:modelValue', value);
			}
		}
	}
};
</script>
