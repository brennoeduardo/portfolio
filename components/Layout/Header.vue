<template>
  <v-app-bar :elevation="0"  color="black">
    <v-app-bar-title>
      <v-img src="/logo_light.png" height="250" width="200" />
    </v-app-bar-title>
    <v-main class="d-flex align-center main">
      <v-btn color="#30AEFF" variant="plain" class="font-weight-bold">
        Home
      </v-btn>
      <v-btn color="#30AEFF" variant="plain" class="font-weight-bold">
        Sobre
      </v-btn>
      <v-btn color="#30AEFF" variant="plain" class="font-weight-bold">
        Projetos
      </v-btn>
      <v-btn color="#30AEFF" variant="plain" class="font-weight-bold">
        Contatos
      </v-btn>
    </v-main>

    <v-btn @click="toggle" :icon="setIcon" :color="setColor"> </v-btn>
  </v-app-bar>
</template>

<script setup>
const light = ref(false);

const toggle = () => {
  light.value = !light.value;
};

const setIcon = computed(() => {
  if (light.value) {
    return "mdi-weather-sunny";
  }
  return "mdi-weather-night";
});

const setColor = computed(() => {
  if (light.value) {
    return "yellow";
  }
  return "blue";
});
</script>

<style scoped>
.main {
  margin-top: -45px;
}
</style>