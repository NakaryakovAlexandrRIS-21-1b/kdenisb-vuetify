<template>
  <div v-for="card in INFO[page]" :key='card.title'>
    <div />
    <a class="link"  :href="card.file" target="_blank">
      <v-card class="ma-6 pa-2 d-flex align-center">
        <div class="d-flex align-center" v-if="card.icon !== 'youtube'">
          <div>
            <v-img :width="50" :src="`icons/${card.icon}.png`"></v-img>
          </div>
          <div>
            <p class="text-h6 ml-4">{{ card.title }}</p>
            <v-card-subtitle>{{ card.subtitle }}</v-card-subtitle>
          </div>
        </div>
      <div class="w-100 overflow-hidden" v-if="card.icon === 'youtube'">
        <div class="d-flex">
          <div>
            <v-img :width="50" :src="`icons/${card.icon}.png`"></v-img>
          </div>
          <div>
            <p class="text-h6 ml-4">{{ card.title }}</p>
            <v-card-subtitle>{{ card.subtitle }}</v-card-subtitle>
          </div>
        </div>
        <div class="d-flex justify-center">
          <iframe
            width="560"
            height="315"
            :src="card.file"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
          />
        </div>

      </div>


      </v-card>
    </a>
  </div>


</template>

<script setup>
import { ref, watch } from "vue"
import { useRoute } from 'vue-router';
import { INFO } from '@/constants.js'
import router from "@/router";

const route = useRoute();
const page = ref(route.params.page)
if(!Object.keys(INFO).includes(page.value.toString())) router.push({name:'errorPage'})
watch(route, (newPage) => {
  page.value = newPage.params.page
  console.log(Object.keys(INFO).includes(page.value.toString()))

})

</script>

<style scoped>
.link{
  text-decoration: none;
}
</style>