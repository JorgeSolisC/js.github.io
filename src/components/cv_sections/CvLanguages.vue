<template>
	<section>
		<h2 class="text-2xl font-bold text-secondary mb-4 flex items-center">
			<i class="pi pi-language mr-3 text-primary" />
			<span>{{ $t('languages') }}</span>
		</h2>
		<div class="space-y-3">
			<div v-for="(lang, index) in languages" :key="index">
				<div class="flex justify-between mb-1">
					<span class="font-medium text-dark">{{ lang.name }}</span>
					<span class="text-sm text-text">{{ lang.level }}</span>
				</div>
				<div class="w-full bg-gray-200 skill-bar">
					<div class="bg-primary skill-bar" :style="{ width: '100%' }" />
				</div>
			</div>
		</div>
	</section>
</template>

<script setup>
defineProps({
    languages: { type: Array, default: () => [] },
    
})
</script>
