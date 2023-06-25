<template>
  <ion-header>
    <ion-toolbar>
      <ion-back-button>The Page Two</ion-back-button>
    </ion-toolbar>
  </ion-header>

  <ion-nav-link :component="PageThree" router-direction="forward">
    <ion-button>Go to Page Three</ion-button>
  </ion-nav-link>
</template>

<script setup lang="ts">
import PageThree from "@/views/PageThree.vue";
import {IonButton, IonNavLink,IonBackButton} from "@ionic/vue";
</script>

<style scoped>

</style>
