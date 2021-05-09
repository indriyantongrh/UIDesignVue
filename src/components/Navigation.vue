<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      dark
      src="@/assets/img/bgDrawer.jpg"
    >
      <v-list>
        <v-list-item>
          <v-toolbar-title>
        <v-img src="@/assets/img/logo.png" max-width="120px" />
      </v-toolbar-title>
          <!-- untuk tittle di -->
          <!-- <v-list-item-content>
            <v-list-item-title class="title">acarain.com</v-list-item-title>
          
          </v-list-item-content> -->
        </v-list-item>
      </v-list>

      <v-divider />

      <v-list dense>
        <v-list-item
          v-for="([icon, text, link], i) in items"
          :key="i"
          link
          @click="$vuetify.goTo(link)"
        >
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      :color="color"
      :flat="flat"
      dark
      class="px-15"
      :class="{ expand: flat }"
    >
      <v-toolbar-title>
        <v-img src="@/assets/img/logo.png" max-width="200px" />
      </v-toolbar-title>
      <v-spacer />
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="mr-4"
        v-if="isXs"
      />
      <div v-else>
        <v-btn text color="#4C8ADD" @click="$vuetify.goTo('#hero')">
          <span class="mr-2">Hi! Selamat Datang</span>
        </v-btn>
        <!-- <v-btn text color="#4C8ADD" @click="$vuetify.goTo('#features')">
          <span class="mr-2">Sobre</span>
        </v-btn> -->
        <v-btn text color="#4C8ADD" @click="$vuetify.goTo('#download')">
          <span class="mr-2">Download App</span>
        </v-btn>
        <!-- <v-btn text color="#4C8ADD" @click="$vuetify.goTo('#pricing')">
          <span class="mr-2">Preços</span>
        </v-btn>
        <v-btn rounded outlined text @click="$vuetify.goTo('#contact')">
          <span class="mr-2">Contate-nos</span>
        </v-btn> -->
      </div>
    </v-app-bar>
  </div>
</template>

<style scoped>
.v-toolbar {
  transition: 0.6s;
}

.expand {
  height: 80px !important;
  padding-top: 10px;
}
</style>

<script>
export default {
  data: () => ({
    drawer: null,
    isXs: false,
    items: [
      ["mdi-home-outline", "Home", "#hero"],
      ["mdi-information-outline", "Sobre", "#features"],
      ["mdi-download-box-outline", "Download", "#download"],
      ["mdi-currency-usd", "Preços", "#pricing"],
      ["mdi-email-outline", "Contatos", "#contact"]
    ]
  }),
  props: {
    color: String,
    flat: Boolean
  },
  methods: {
    onResize() {
      this.isXs = window.innerWidth < 850;
    }
  },

  watch: {
    isXs(value) {
      if (!value) {
        if (this.drawer) {
          this.drawer = false;
        }
      }
    }
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize, { passive: true });
  }
};
</script>
