<template>
	<div class="bg-secondary text-white p-8 md:p-10">
		<div class="flex flex-col md:flex-row items-center gap-8">
			<div class="w-32 h-32 rounded-full border-4 border-primary overflow-hidden shadow-lg">
				<img src="@/assets/images/profile.png" alt="Profile" class="w-full h-full object-cover" />
			</div>
			<div class="flex-1 text-center md:text-left">
				<h1 class="text-3xl md:text-4xl font-bold mb-2">Jorge Armando Solis Cruz</h1>
				<p class="text-xl opacity-90 mb-4">{{ position }}</p>
				<div class="flex flex-wrap justify-center md:justify-start gap-4 text-sm">
					<div class="flex items-center">
						<i class="pi pi-envelope mr-2 text-primary" />
						<span>jorgearmando.soliscruz@gmail.com</span>
					</div>
					<div class="flex items-center">
						<i class="pi pi-phone mr-2 text-primary" />
						<span>+52 (346) 100-4832</span>
					</div>
					<div class="flex items-center">
						<i class="pi pi-map mr-2 text-primary" />
						<span>Aguascalientes, Ags, México.</span>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script setup>
defineProps({
    position: { type: String, default: () => '' },
})
</script>