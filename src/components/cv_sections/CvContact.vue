<template>
	<section>
		<h2 class="text-2xl font-bold text-secondary mb-4 flex items-center">
			<i class="pi pi-bookmark mr-3 text-primary" />
			<span>{{ $t('contact') }}</span>
		</h2>
		<div class="space-y-3">
			<div class="flex items-center">
				<div
					class="w-10 h-10 rounded-full bg-primary bg-opacity-10 text-primary flex items-center justify-center mr-3">
					<i class="pi pi-linkedin text-white" />
				</div>
				<a :href="'https://' + socialLinks.linkedin" target="_blank" class="text-dark hover:text-primary">{{
					socialLinks.linkedin }}</a>
			</div>
			<div class="flex items-center">
				<div
					class="w-10 h-10 rounded-full bg-primary bg-opacity-10 text-primary flex items-center justify-center mr-3">
					<i class="pi pi-github text-white" />
				</div>
				<a :href="'https://' + socialLinks.github" target="_blank" class="text-dark hover:text-primary">{{
					socialLinks.github }}</a>
			</div>
		</div>
	</section>
</template>

<script setup>
defineProps({
    socialLinks: { type: Object, default: () => null },
})
</script>