<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>{{ $route.params.id }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-nav-link router-direction="forward" :component="PageTwo" :router-animation="getRouterAnimation">
        <ion-button>Go to Page Two</ion-button>
      </ion-nav-link>
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">{{ $route.params.id }}</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <strong class="capitalize">{{ $route.params.id }}</strong>
        <p>Explore <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonNavLink,
  IonButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonMenuButton,
  IonPage,
  IonTitle,
  IonToolbar,
  createAnimation
} from '@ionic/vue';
import PageTwo from "@/views/PageTwo.vue";
const getRouterAnimation = (baseEl: any, opts: any) => {
  console.log("opts", opts);
  const rootTransition = createAnimation()
      .addElement(baseEl)
      .duration(opts.duration || 333);

  const enterTransition = createAnimation().addElement(opts.enteringEl);
  const exitTransition = createAnimation().addElement(opts.leavingEl);

  enterTransition.fromTo('opacity', '0', '1');
  exitTransition.fromTo('opacity', '1', '0');

  if (opts.direction === 'forward') {
    enterTransition.fromTo('transform', 'translateX(-1.5%)', 'translateX(0%)');
    exitTransition.fromTo('transform', 'translateX(0%)', 'translateX(1.5%)');
  } else {
    enterTransition.fromTo('transform', 'translateX(1.5%)', 'translateX(0%)');
    exitTransition.fromTo('transform', 'translateX(0%)', 'translateX(-1.5%)');
  }
  rootTransition.addAnimation([enterTransition, exitTransition]);
  return rootTransition;
};
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
