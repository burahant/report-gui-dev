<template>
  <v-app>
    <v-app-bar app color="#004aad" dark>
      <div class="d-flex align-center">
        <v-img alt="Report GUI Logo" class="shrink mr-2" contain src="./assets/report-gui-nobackground.png" transition="scale-transition" width="200" height="65" />
        <!-- <span>Report GUI 1.0</span> -->
      </div>

      <v-spacer></v-spacer>

      <div class="nes-text league-spartan mr-2">
        <v-icon>mdi-github</v-icon>
        <span> Github</span>
      </div>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style scoped>
.press-start-2p-regular {
  font-family: 'Press Start 2P', system-ui;
  font-weight: 400;
  font-style: normal;
}
.league-spartan {
  font-family: 'League Spartan', sans-serif;
  font-optical-sizing: auto;
  font-weight: 600;
  font-style: normal;
}
</style>

<script>
export default {
  name: 'App',

  data: () => ({
    //
  })
}
</script>
