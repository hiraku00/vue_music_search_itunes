<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Search Result
        </h1>
        <p>
          Search Keyword : {{ $route.params.keyword }}
        </p>
        <v-card
          max-width="400"
          class="mx-auto"
        >
          <v-container>
            <v-row dense>
              <v-col>
                <div style="margin-bottom:10px" v-for="(album, i) in albums" :key="i">
                <v-card
                  dark
                  :href="album.collectionViewUrl"
                  target="_blank"
                  >
                  <div class="d-flex flex-no-wrap justify-space-between">
                    <div>
                      <v-card-title
                        class="headline"
                        v-text="album.collectionName"
                      ></v-card-title>

                      <v-card-subtitle v-text="album.artistName"></v-card-subtitle>
                    </div>

                    <v-avatar
                      class="ma-3"
                      size="125"
                      tile
                    >
                      <v-img :src="album.artworkUrl100"></v-img>
                    </v-avatar>
                  </div>
                </v-card>
                </div>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      albums: [],
    }
  },
  created() {
    const vm = this
    axios.get(`https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`)
      .then(response => {
        console.log(response)
        vm.albums = response.data.results
      })
  }
}
</script>
