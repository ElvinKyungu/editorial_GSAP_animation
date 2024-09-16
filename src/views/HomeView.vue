<script setup lang="ts">
import { ref } from 'vue'
import { gsap } from 'gsap'
import { Flip } from 'gsap/Flip'
import CardImage from '@/components/base/CardImage.vue'

// Enregistrement du plugin Flip
gsap.registerPlugin(Flip)

// Importation des images
import img1 from '@/assets/img1.webp'
import img2 from '@/assets/img2.webp'
import img3 from '@/assets/img3.webp'
import img4 from '@/assets/img4.avif'
import img5 from '@/assets/img5.avif'
import img6 from '@/assets/img6.avif'
import img7 from '@/assets/img7.avif'
import img8 from '@/assets/img8.avif'
import img9 from '@/assets/img9.avif'
import img10 from '@/assets/img10.avif'
import img11 from '@/assets/img11.avif'
import img12 from '@/assets/img12.avif'

// Tableau d'images
const images = [
  { src: img1 },
  { src: img2 },
  { src: img3 },
  { src: img4 },
  { src: img5 },
  { src: img6 },
  { src: img7 },
  { src: img8 },
  { src: img9 },
  { src: img10 },
  { src: img11 },
  { src: img12 }
]

// Références pour l'image principale et l'image cliquée
const mainImage = ref(img4)
const mainImageEl = ref<HTMLElement | null>(null)

// Fonction de gestion du clic d'image
const handleImageClick = (imageSrc: string, cardEl: HTMLElement) => {
  // Enregistrer l'état initial avant l'animation
  const state = Flip.getState([mainImageEl.value, cardEl])

  // Mettre à jour l'image principale
  mainImage.value = imageSrc

  // Déclencher l'animation de transition de l'image
  Flip.from(state, {
    duration: 1,
    ease: 'power2.inOut',
    absolute: true, // Activer le positionnement absolu pour une transition fluide
    scale: true, // Inclure la mise à l'échelle dans l'animation
    onEnter: (elements) => {
      gsap.fromTo(elements, { opacity: 0 }, { opacity: 1, duration: 0.5 }) // Animation d'apparition de l'image
    },
    onLeave: (elements) => {
      gsap.to(elements, { opacity: 0, duration: 0.5 }) // Animation de disparition de l'ancienne image
    }
  })
}
</script>

<template>
  <main class="px-32 py-10 space-y-16 flex flex-col font-poppins">
    <!-- Première section avec l'image principale -->
    <section class="grid grid-cols-12 gap-5 h-[70vh]">
      <div class="col-span-5 flex flex-col justify-between relative">
        <p class="uppercase">Made by Elvin Code</p>
        <div class="relative">
          <p class="-mb-5">
            <span class="font-bold">01</span><span class="text-gray-600">/05</span>
          </p>
          <h1 class="text-[8rem] -ml-5 uppercase font-bold flex flex-col space-y-[-5rem]">
            <span>Editorial</span>
            <span>By Hasse</span>
            <span>Nielsen.</span>
          </h1>
        </div>
      </div>

      <!-- Image principale -->
      <div class="col-span-7 flex flex-col justify-between">
        <div class="relative w-full h-[70vh]">
          <img
            ref="mainImageEl"
            :src="mainImage"
            alt="Main Editorial Image"
            class="absolute w-full h-full object-cover"
          />
        </div>
        <p class="flex justify-between mt-3 uppercase">
          <span class="border-b border-black">WOMEN MK GUCCI</span>
          <span class="border-b border-black">VIEW MORE</span>
        </p>
      </div>
    </section>

    <!-- Section des images miniatures -->
    <section>
      <div class="grid grid-cols-12 gap-4">
        <CardImage
          v-for="(image, index) in images"
          :key="index"
          :index="index + 1"
          :src="image.src"
          @click="(e) => handleImageClick(image.src, e.currentTarget)"
        />
      </div>
    </section>
  </main>
</template>
