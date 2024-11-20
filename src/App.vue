<template>
  <v-app>
    <v-navigation-drawer app flat permanent expand-on-hover :mini-variant.sync="mini" v-model="drawer">
      <!-- Sidebar content here -->

      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-icon>mdi-security</v-icon>
          <!-- <v-img src="./assets/snorlax.png"></v-img> -->
        </v-list-item-avatar>

        <v-list-item-title>Administrator</v-list-item-title>

        <v-btn icon @click.stop="mini = !mini">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-list dense>
        <v-list-item v-for="item in items" :key="item.title" link @click="navigate(item.route)">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <!-- Add more items as needed -->
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app flat>
      <v-toolbar-title class="d-flex align-center">
        <router-link to="/">
          <v-img alt="Report GUI Logo" class="shrink mr-2" contain src="./assets/ration_logo.png" transition="scale-transition" width="200" height="65" />
        </router-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <!-- Search Box -->
      <v-flex xs12 sm6 md4 lg3 class="d-flex align-center">
        <v-text-field v-model="search" prepend-inner-icon="mdi-magnify" label="Type / to search" dense single-line hide-details outlined class="flex-grow-1 mr-6 custom-search-box"></v-text-field>
      </v-flex>
      <v-divider vertical inset></v-divider>

      <!-- First Dropdown Button -->
      <v-menu offset-y open-on-hover close-delay transition="scale-transition" bottom left>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" text class="no-uppercase no-bold ml-2">
            Generation
            <v-icon right>mdi-menu-down</v-icon>
          </v-btn>
        </template>
        <v-card>
          <v-card-text class="dense-card-text">
            <v-list dense>
              <v-list-item @click="handleAction('action1')">
                <v-list-item-title>Generation 1</v-list-item-title>
              </v-list-item>
              <v-list-item @click="handleAction('action2')">
                <v-list-item-title>Generation 2</v-list-item-title>
              </v-list-item>
              <v-list-item @click="handleAction('action3')">
                <v-list-item-title>Generation 3</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
      </v-menu>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({
    drawer: false,
    mini: true,
    items: [
      { title: 'Home', icon: 'mdi-home-circle-outline', route: '/' },
      { title: 'About', icon: 'mdi-information-outline', route: '/about' },
      { title: 'Github Repository', icon: 'mdi-github', route: 'https://github.com/burahant/report-gui-dev' }
    ],
    search: ''
  }),
  methods: {
    navigate(route) {
      // Check if route is an external URL
      if (route.startsWith('http')) {
        window.open(route, '_blank')
      } else {
        // Navigate using Vue Router
        if (this.$route.path !== route) {
          this.$router.push(route)
        }
      }
    }
  }
}
</script>

<style scoped>
.no-uppercase {
  text-transform: none !important;
}

.no-bold {
  font-weight: normal !important;
}

.dense-card-text {
  font-size: 14px;
  font-weight: 700;
  padding-top: 0%;
  padding-bottom: 0%;
  padding-left: 5%;
  padding-right: 5%;
}
</style>
