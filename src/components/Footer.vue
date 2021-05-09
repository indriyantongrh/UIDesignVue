<template>
  <v-footer dark padless>
    <v-card flat tile class="secondary white--text text-center">
      <v-card-text>
        <v-btn
          v-for="(icon, i) in icons"
          :key="i"
          class="mx-4 white--text"
          :href="icon.link"
          target="_blank"
          icon
        >
          <v-icon size="24px">{{ icon.text }}</v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        <v-row align="center" justify="center">
         <v-col cols="10">
          <v-row justify="center" align="center"  >
            <div >
              <a target="blank_" href="https://play.google.com/store">
                <v-img max-width="150px" src="~@/assets/img/playstore.png"></v-img>
                 </a>
            </div>
            <div >
              <a target="blank_" href="https://www.apple.com/app-store/">
                <v-img max-width="160px"  src="~@/assets/img/appstore.png" />
                </a>
            </div>
          </v-row>
            </v-col>
      </v-row>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        © acarain.com  {{ new Date().getFullYear() }}. | Temukan acara minatmu sekarang!
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<style scoped>
.v-card {
  width: 100%;
}
</style>

<script>
export default {
  data: () => ({
    icons: [
      {
        text: "mdi-facebook",
        link: ""
      },
      {
        text: "mdi-twitter",
        link: ""
      },
      {
        text: "mdi-linkedin",
        link: ""
      },
      {
        text: "mdi-instagram",
        link: "https://instagram.com/joabson_arley/"
      }
    ]
  })
};
</script>
