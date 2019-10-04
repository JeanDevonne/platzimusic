<template lang="pug">
  #app
    img(src='https://jeandevonne.github.io/platzimusic/dist/logo.png')
    h1 PlatziMusic
    select(v-model="selectedCountry")
      option(v-for="country in countries" v-bind:value="country.value") {{ country.name }}
    spinner(v-show="loading")
    ul
      artist(v-for="artist in artists" v-bind:artist="artist" v-bind:key="artist.mbid")
</template>

<script>
import Artist from './components/Artist'
import Spinner from './components/Spinner'
import getArtists from './api'

export default {
  name: 'app',
  data () {
    return {
      artists: [],
      countries: [
        { name: 'Peru', value: 'peru' },
        { name: 'Argentina', value: 'argentina' },
        { name: 'Colombia', value: 'colombia' },
        { name: 'España', value: 'spain' }
      ],
      selectedCountry: 'peru',
      loading: true
    }
  },
  components: {
    Artist: Artist,
    Spinner: Spinner
  },
  methods: {
    refreshArtists() {
      const self = this
      this.loading = true
      getArtists(this.selectedCountry)
        .then(function(artists) {
          self.artists = artists
<<<<<<< HEAD
          self.loading = false
=======
          selt.loading = false
>>>>>>> 9dddaf6c6682626598222773c54d13e834085746
        })
    }
  },
  mounted() {
    this.refreshArtists()
  },
  watch: {
    selectedCountry(){
      this.refreshArtists()
    }
  }
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

h1, h2
  font-weight normal

ul
  list-style-type none
  padding 0

li
  display inline-block
  margin 0 10px

a
  color #42b983
</style>
