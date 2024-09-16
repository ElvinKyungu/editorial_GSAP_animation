<script setup lang="ts">
defineProps({
  index: Number,
  src: String
});
</script>

<template>
  <div class="card-img">
    <p>{{ index?.toString().padStart(2, '0') }}</p>
    <img :src="src" alt="" class="img" />
  </div>
</template>

<style>
.img {
  @apply col-span-1 h-28 w-full object-cover;
}

.card-img {
  @apply flex justify-between flex-col items-center;
}
</style>