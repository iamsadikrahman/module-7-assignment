<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const items = ref([
  'https://source.unsplash.com/random?tiger',
  'https://source.unsplash.com/random?technology',
  'https://source.unsplash.com/random?mountain',
  'https://source.unsplash.com/random?art',
  'https://source.unsplash.com/random?cat',
  'https://source.unsplash.com/random?bird',
  'https://source.unsplash.com/random?animal',
  'https://source.unsplash.com/random?fish',
])

let carousel = null


onMounted(()=>{
  carousel = new Flickity('#carousel',{})
})

onBeforeUnmount(() => {
  if (carousel) {
    carousel.destroy();
  }
})

</script>

<template>

    <h1 class="text-4xl">Carousel Slider</h1>
    
  <div class="mx-auto items" id="carousel">
    <div :style="`background-image:url(${item})`" class="item" v-for="item, index in items" :key="item"></div>
  </div>
 
  
</template>

<style scoped>
.items {
  width: 600px;
  height: 400px;
}

.item {
  width: 600px;
  height: 400px;
  background-color: #ccc;
  background-size: cover;
}
</style>
