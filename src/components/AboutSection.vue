<template>
  <section id="about">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col >
              <v-row>
                <div class="row mt-4">
        <div class="col">
          <h1>
            Acara
            <strong>Populer</strong>
          </h1>
        </div>
                </div>
      <!-- <v-row>
      <div class="row mt-4">
        <div class="col">
          <h1>
            Acara
            <strong>Populer</strong>
          </h1>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-success float-right">
            <b-icon-eye></b-icon-eye>Lihat Semua
          </router-link>
        </div>
      </div>
      </v-row> -->

          <v-row class="flex-nowrap" no-gutter h v-for="(feature, i) in features"
              :key="i" >
                <v-col cols="10">
              <v-hover v-slot:default="{ hover }">
            <v-card class="mt-5" max-width="300px" :elevation="hover ? 10 : 4"
                  :class="{ up: hover }" >
              <v-img height="200" class="black--text align-end" :src="feature.img">
              </v-img>
              <v-card-title>{{ feature.title }}</v-card-title>
              <v-card-subtitle class="pb-0"> {{ feature.attended}} | {{ feature.date}} | {{feature.category}} </v-card-subtitle>
              <v-spacer></v-spacer>
              <v-card-text class="text--primary">{{feature.text}}
              </v-card-text>
              <v-divider></v-divider>
              <v-card-actions class="justify-end" >
                <v-btn color="accent"
            elevation="5"
            outlined plain
             >Lihat Event</v-btn>
                 </v-card-actions>
            </v-card>
              </v-hover>
               </v-col>
          </v-row>

              </v-row>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>


<script>
export default {
   data () {
    return {
      province: [],
      info: null,
      loading: true,
      errored: false
    }
  },
  mounted(){
    axios
      .get('http://api-beta.acarain.com/api/get_province')
      .then(response => {
        this.province = response.data.data_province
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)

  },

  data() {
    return {
      dialog: false,
      videoId: "i8IvvHJssWE",
      features: [
        {
          img: "http://api-beta.acarain.com/images_event/image_picker909976312009677068-1610113351.jpg",
          title: "Kumpul Bareng Kuy",
          attended: "30 Hadir",
          date: "09/01/2021",
          category: "Seminar",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
        },
        {
          img: "http://api-beta.acarain.com/images_event/image_picker909976312009677068-1610113351.jpg",
          title: "Dados Seguros",
            attended: "30 Hadir",
          date: "09/01/2021",
          category: "Seminar",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
        },
        {
          img: "http://api-beta.acarain.com/images_event/image_picker909976312009677068-1610113351.jpg",
          title: "Código Aberto",
            attended: "30 Hadir",
          date: "09/01/2021",
          category: "Seminar",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
        },
           {
          img: "http://api-beta.acarain.com/images_event/image_picker909976312009677068-1610113351.jpg",
          title: "Código Aberto",
            attended: "30 Hadir",
          date: "09/01/2021",
          category: "Seminar",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit."
        }, 
      ]
    };
  },
  watch: {
    dialog(value) {
      if (!value) {
        this.pause();
      }
    }
  },
  methods: {

    ready(event) {
      this.player = event.target;
    },
    playing(event) {
      // The player is playing a video.
    },
    change() {
      // when you change the value, the player will also change.
      // If you would like to change `playerVars`, please change it before you change `videoId`.
      // If `playerVars.autoplay` is 1, `loadVideoById` will be called.
      // If `playerVars.autoplay` is 0, `cueVideoById` will be called.
      this.videoId = "another video id";
    },
    stop() {
      this.player.stopVideo();
    },
    pause() {
      this.player.pauseVideo();
    }
  }

};
</script>


<style scoped>
#about {
  background-color: #f4f7f5;
}
.horizontal-scroll-wrapper {
  width: 100px;
  height: 300px;
  overflow-y: auto;
  overflow-x: hidden;
   transform: rotate(-90deg);
  transform-origin: right top;
}
.horizontal-scroll-wrapper > div {
  width: 100px;
  height: 100px;
  transform: rotate(90deg);
  transform-origin: right top;
}

</style>
