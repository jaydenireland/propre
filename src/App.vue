<script setup lang="ts">
import Button from '@/components/atoms/Button.vue';
import Checkbox from '@/components/atoms/Checkbox.vue';
import Radio from '@/components/atoms/Radio.vue';
import Input from '@/components/atoms/Input.vue';
import Alert from '@/components/atoms/Alert.vue';

import { ref } from 'vue';

const buttonText = ref('Button Text');
const checkboxValue = ref(false);
const radioValue = ref(false);

const showButtonVarient = ref('solid');
const showButtonDisabled = ref(false);

const breadcrumbItems = ref([
  { text: 'Home', link: '/' },
  { text: 'Category', action: () => console.log('Category clicked') },
  { text: 'Product', link: '/product' }
]);
</script>

<template>


	<div class="p-4 flex flex-col gap-4" v-if="true">
		<!-- Buttons -->
		<div>
			<h1 class="text-3xl font-bold py-4">Buttons</h1>
			<Input required="true" type="text" v-model="buttonText" label="Button Text" />
			<template v-for="variant in ['solid', 'outline']" :key="variant">
				<template v-for="disabled in [false, true]" :key="disabled">
					<template v-if="showButtonVarient === variant && showButtonDisabled === disabled">
						<div class="flex gap-2">
							<Button>
								<p @click="showButtonVarient = variant === 'solid' ? 'outline' : 'solid'">
									{{ variant }}
								</p>
							</Button>
							<Button>
								<p @click="showButtonDisabled = !showButtonDisabled">
									{{ disabled ? 'Disabled' : 'Not Disabled' }}
								</p>
							</Button>
						</div>
						<div class="grid grid-cols-3 gap-4 py-4">
							<Button @click="console.log({ variant, disabled })" :variant="variant" :disabled="disabled" status="primary">{{ buttonText }}</Button>
							<Button :variant="variant" :disabled="disabled" status="success">{{ buttonText }}</Button>
							<Button :variant="variant" :disabled="disabled" status="warning">{{ buttonText }}</Button>
							<Button :variant="variant" :disabled="disabled" status="danger">
								{{ buttonText }}
							</Button>
							<Button :variant="variant" :disabled="disabled" status="neutral">{{ buttonText }}</Button>
						</div>
					</template>
				</template>
			</template>
		</div>

		<!-- Checkbox -->
		<div class="flex flex-col">
			<h1 class="text-3xl font-bold py-4">Checkbox</h1>
			{{ checkboxValue ? 'Checked' : 'Unchecked' }}
			<Checkbox v-model="checkboxValue" />
		</div>

		<!-- Radio -->
		<div class="flex flex-col">
			<h1 class="text-3xl font-bold py-4">Checkbox</h1>
			{{ radioValue ? 'Checked' : 'Unchecked' }}
			<Radio v-model="radioValue" />
		</div>

		<Alert status="success">
			<p>Success</p>
		</Alert>
	</div>
</template>

<style scoped>
header {
	line-height: 1.5;
}

.logo {
	display: block;
	margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
		padding-right: calc(var(--section-gap) / 2);
	}

	.logo {
		margin: 0 2rem 0 0;
	}

	header .wrapper {
		display: flex;
		place-items: flex-start;
		flex-wrap: wrap;
	}
}
</style>
