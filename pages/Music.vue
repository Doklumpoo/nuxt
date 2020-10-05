<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col />
      <v-col>
        <v-img
          src="https://www.macthai.com/wp-content/uploads/2015/07/itunes-12-2-new-icon.png"
          class="img-fluid mx-auto"
        />
      </v-col>
      <v-col />
    </v-row>
    <v-row justify="center" align="center">
      <v-col />
      <v-col>
        <br />
        <br />
        <v-row justify="center" align="center">
          <v-text-field
            v-model="keyword"
            class="white--text"
            label="Filled"
            filled
            rounded
            dense
            single-line
            type=" text"
            placeholder="Please enter the name of the song you want to search."
          />
        </v-row>
        <v-row justify="center" align="center"
          ><v-btn
            color="red"
            dark
            filled
            rounded
            v-bind="attrs"
            v-on="on"
            @click="searchData"
          >
            <v-icon>mdi-magnify</v-icon>
          </v-btn></v-row
        >
        <v-row justify="center" align="center" />
      </v-col>
      <v-col />
    </v-row>
    <v-row>
      <v-col
        v-for="data in resultData"
        :key="data.trackId"
        justify="center"
        align="center"
      >
        <v-card
          :title="data.title"
          hide-details
          label="Filled"
          filled
          rounded
          dense
          single-line
        >
          <v-card-text>
            {{ data.trackName }}
          </v-card-text>
          <nuxt-link :to="{ name: 'shop-id', params: { id: data } }">
            <v-img :src="data.artworkUrl100" max-height="100" max-width="100" />
          </nuxt-link>
          <v-card-text>
            {{ data.artistName }}
          </v-card-text>
          <audio controls>
            <source :src="data.previewUrl" type="audio/mpeg" />
          </audio>
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
      resultData: null,
      keyword: '',
    }
  },
  methods: {
    searchData() {
      axios
        .get(
          'https://itunes.apple.com/search?term=' + this.keyword + '&limit=30'
        )
        .then((response) => {
          this.resultData = response.data.results
        })
    },
  },
}
</script>

<style>
.theme--dark.v-application {
  background-image: url('https://cdn.discordapp.com/attachments/746260527235334237/761540128077512704/dark-bg.jpg');
  background-attachment: fixed;
  background-position: 100% 100%;
  background-repeat: no-repeat;
  background-size: cover;
}
.theme--dark.v-card {
  background-image: url('https://cdn.discordapp.com/attachments/746260527235334237/761540690856378388/3000x3000-hd-icon-bg-dark-v2.jpg');
  background-attachment: fixed;
  background-position: 100% 100%;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
