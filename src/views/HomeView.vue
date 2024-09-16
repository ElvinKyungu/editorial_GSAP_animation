<script setup lang="ts">
import CardImage from '@/components/base/CardImage.vue'

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
</script>
<template>
  <main class="px-32 py-10 space-y-16 flex flex-col font-poppins">
    <section class="grid grid-cols-12 gap-5 h-[70vh]">
      <div class="col-span-5 flex flex-col justify-between relative">
        <p class="uppercase">Made by Elvin Code</p>
        <div class="relative">
          <p class="-mb-5">
            <span class="font-bold">01</span><span class="text-gray-600">/05</span>
          </p>
          <h1 class=" text-[8rem] -ml-5 uppercase font-bold flex flex-col space-y-[-5rem] ">
            <span>Editorial</span>
            <span>By Hasse</span>
            <span>Nielsen.</span>
          </h1>
        </div>
      </div>
      <div class="col-span-7 flex flex-col justify-between">
        <div class="relative w-full h-[70vh]">
          <img
            :src="img4"
            alt="Editorial Image"
            class="absolute w-full h-full object-cover"
          />
        </div>
        <p class="flex justify-between mt-3 uppercase ">
          <span class="border-b border-black">WOMEN MK GUCCI</span>
          <span class="border-b border-black">VIEW MORE</span>
        </p>
      </div>
    </section>
    <section>
      <div class="grid grid-cols-12 gap-4">
        <CardImage v-for="(image, index) in images" :key="index" :index="index + 1" :src="image.src" />
      </div>
    </section>
  </main>
</template>