<template>
	<section>
		<h2 class="text-2xl font-bold text-secondary mb-4 flex items-center">
			<i class="pi pi-user mr-3 text-primary" />
			<span>{{ $t('about') }}</span>
		</h2>
		<p class="text-text leading-relaxed text-justify">
			{{ aboutText }}
		</p>
	</section>
</template>

<script setup>
defineProps({
    aboutText: { type: String, default: () => '' },
})
</script>
