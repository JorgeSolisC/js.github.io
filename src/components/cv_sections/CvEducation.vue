<template>
	<section>
		<h2 class="text-2xl font-bold text-secondary mb-4 flex items-center">
			<i class="pi pi-graduation-cap mr-3 text-primary" />
			<span>{{ $t('education') }}</span>
		</h2>
		<div class="space-y-6">
			<div v-for="(edu, index) in education" :key="index" class="relative pl-8 timeline-item">
				<div
					class="absolute left-0 top-0 w-6 h-6 rounded-full bg-primary border-4 border-light flex items-center justify-center">
					<div class="w-2 h-2 rounded-full bg-white" />
				</div>
				<div class="bg-light p-6 rounded-lg border border-light">
					<h3 class="text-xl font-semibold text-dark">{{ edu.degree }}</h3>
					<div class="flex flex-wrap items-center text-text text-sm mb-2">
						<span class="mr-4"><i class="pi pi-book mr-1 text-primary" /> {{
							edu.institution }}</span>
						<span><i class="pi pi-calendar mr-1 text-primary" /> {{ edu.period
						}}</span>
					</div>
					<p class="text-text">{{ edu.description }}</p>
				</div>
			</div>
		</div>
	</section>
</template>

<script setup>
defineProps({
    education: { type: Array, default: () => [] },
    
})
</script>