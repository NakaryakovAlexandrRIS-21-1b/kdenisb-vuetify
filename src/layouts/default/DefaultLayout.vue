<template>
  <v-app>
    <v-app-bar :elevation="2" color="primary">
      <template v-slot:prepend>
        <v-app-bar-nav-icon @click="togleDrawer" />
      </template>
      <v-app-bar-title class="name">Кузнецов Денис Борисович</v-app-bar-title>
      <template v-slot:append>
        <div class="d-flex ga-2 align-center">
          <p>Контакты:</p>
          <a href="https://vk.com/kdenisb" target="_blank">
            <v-img
              src="@/assets/icons/vk.svg"
              type="img"
              :width="40"
              class="contact-btn"
            />
          </a>
          <a href="https://gmail.com" target="_blank">
            <v-img
              src="@/assets/icons/gmail.svg"
              href="google.com"
              type="img"
              :width="40"
              class="contact-btn"
            />
          </a>
          <a href="https://t.me/to_the_summer" target="_blank">
            <v-img
              src="@/assets/icons/telegram.svg"
              href="google.com"
              type="img"
              :width="40"
              class="contact-btn"
            />
          </a>
        </div>
      </template>
    </v-app-bar>
    <v-navigation-drawer v-model="isOpened" :width="310">
        <v-list>
          <v-list-item
          :class="{'bg-primary': nav.path === route.path}"
          v-for="nav in DRAWER_NAV"
          :key="nav.id"
          :title="nav.name"
          @click="router.push(nav.path)"
        ></v-list-item>
        </v-list>

    </v-navigation-drawer>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
import { DRAWER_NAV } from "@/constants"
import router from "@/router";
import {useRoute} from "vue-router";
const isOpened = ref(window.innerWidth >= 1280);
const route = useRoute()
const togleDrawer = () => {
  isOpened.value = !isOpened.value;
};
</script>

<style>
@media (max-width: 650px) {
  .name {
    display: none;
  }
}
.contact-btn {
  cursor: pointer;
}
</style>
