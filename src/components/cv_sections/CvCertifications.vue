<template>
	<section>
		<h2 class="text-2xl font-bold text-secondary mb-4 flex items-center">
			<i class="pi pi-trophy mr-3 text-primary" />
			<span>{{ $t('certifications') }}</span>
		</h2>
		<div class="space-y-4">
			<div
				v-for="(cert, index) in certifications" :key="index"
				class="bg-light p-4 rounded-lg border border-light">
				<h3 class="font-semibold text-dark">{{ cert.name }}</h3>
				<p class="text-sm text-text mb-1">{{ cert.issuer }}</p>
				<p class="text-xs text-text opacity-70">{{ cert.date }}</p>
			</div>
		</div>
	</section>
</template>

<script setup>
defineProps({
    certifications: { type: Array, default: () => [] },
    
})
</script>
