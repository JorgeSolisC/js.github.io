<template>
	<div id="cv" class="bg-light min-h-screen">
		<div class="container mx-auto px-4 py-8 max-w-6xl">
			<CvControls
				:currentLanguage="currentLanguage"
				@change-language="changeLanguage"
				@open-pdf-modal="() => showPDFModal = true" />

			<div class="bg-white rounded-lg shadow-sm overflow-hidden border border-light">
				<CvHeader
					:position="profileData.position" />

				<div class="grid grid-cols-1 lg:grid-cols-3 gap-8 p-8 md:p-10">
					<div class="lg:col-span-2 space-y-8">
						<CvAbout :aboutText="profileData.aboutText" />
						<CvExperience :experiences="profileData.experiences" :currentLanguage="currentLanguage" />
						<CvEducation :education="profileData.education" :currentLanguage="currentLanguage" />
					</div>

					<div class="space-y-8">
						<CvSkills :skills="profileData.skills" />
						<CvLanguages :languages="profileData.languages" :currentLanguage="currentLanguage" />
						<CvCertifications
							:certifications="profileData.certifications"
							:currentLanguage="currentLanguage" />
						<CvContact :socialLinks="profileData.socialLinks" />
					</div>
				</div>
			</div>
		</div>
		<CVViewer
			:is-visible="showPDFModal"
			:profile-data="profileData"
			@close-pdf="showPDFModal = false" />
	</div>
</template>

<script setup>
import { ref, computed } from 'vue'
import CvControls from '@/components/cv_sections/CvControls.vue'
import CvHeader from '@/components/cv_sections/CvHeader.vue'
import CvAbout from '@/components/cv_sections/CvAbout.vue'
import CvExperience from '@/components/cv_sections/CvExperience.vue'
import CvEducation from '@/components/cv_sections/CvEducation.vue'
import CvSkills from '@/components/cv_sections/CvSkills.vue'
import CvLanguages from '@/components/cv_sections/CvLanguages.vue'
import CvCertifications from '@/components/cv_sections/CvCertifications.vue'
import CvContact from '@/components/cv_sections/CvContact.vue'
import CVViewer from '@/views/CVViewer.vue' 

import { useI18n } from 'vue3-i18n'
import enData from '@/lang/data/en_data.json'
import esData from '@/lang/data/es_data.json'

const i18n = useI18n();

const currentLanguage = ref(localStorage.locale ?? 'en');
const showPDFModal = ref(false) 

const changeLanguage = async () => {
    currentLanguage.value = localStorage.locale = currentLanguage.value === 'es' ? 'en' : 'es';
    i18n.setLocale(currentLanguage.value);
}

const profileData = computed(() => {
  return currentLanguage.value === 'es' ? esData : enData
})

</script>

<style>
@media print {
    #cv {
        width: 100% !important;
    }

    body {
        font-family: Georgia, serif;
        background: white;
        color: black;
        line-height: 1.4;
    }

    .container {
        max-width: 100% !important;
        padding: 0 !important;
    }

    /* Oculta los controles y el resto del CV cuando el modal se está imprimiendo */
    /* La clase 'no-print' es importante aquí */
    .no-print {
        display: none !important;
    }
    /* Asegúrate de que el resto del contenido de la página principal también se oculte */
    #cv > .container {
        display: none;
    }
    /* El CVViewer se encarga de mostrar su propio contenido para imprimir */


    .bg-white,
    .bg-light,
    .bg-secondary,
    .bg-primary,
    .bg-dark {
        background: transparent !important;
        color: black !important;
        box-shadow: none !important;
    }

    .text-primary,
    .text-secondary,
    .text-dark,
    .text-white {
        color: black !important;
    }

    .border,
    .border-light,
    .border-primary {
        border: none !important;
    }

    .rounded-lg,
    .rounded-full,
    .shadow-sm {
        border-radius: 0 !important;
        box-shadow: none !important;
    }

    /* Elimina íconos y decoraciones */
    i,
    .fa,
    .fas,
    .fab {
        display: none !important;
    }

    /* Cambia el encabezado */
    h1 {
        font-size: 28px;
        margin-bottom: 5px;
    }

    h2 {
        font-size: 20px;
        margin-top: 20px;
        border-bottom: 1px solid #000;
        padding-bottom: 2px;
    }

    h3 {
        font-size: 16px;
        margin: 0;
    }

    p {
        font-size: 14px;
        margin-bottom: 6px;
    }

    .timeline-item::after {
        display: none !important;
    }

    .skill-bar {
        display: none !important;
    }

    /* Elimina la foto */
    img {
        display: none !important;
    }

    /* Simplifica los datos de contacto */
    .flex.items-center.gap-8,
    .flex.flex-wrap.justify-center,
    .md\:justify-start {
        flex-direction: column !important;
        align-items: flex-start !important;
        gap: 0 !important;
    }

    a {
        color: black;
        text-decoration: none;
    }
}
</style>