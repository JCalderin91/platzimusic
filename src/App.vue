<template>
  <div id="app">
    <img height="100" src="https://jcalderin91.github.io/platzimusic/dist/logo.png">
    <h1>{{ msg }}</h1>
    <h4>Artistas</h4>
    <div class="artists">
      <div class="artist" v-for="(artist,index) in artists">
        <div class="photo">
          <img height="100" :src="artist.image[1]['#text']">
        </div>
        <h6 class="name">#{{index}} - {{ artist.name }}</h6>
      </div> 
    </div>
  </div>
</template>

<script>
import getArtists from './api'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Platzi Music',
      artists: []
    }
  },
  mounted: function(){
    const self = this
    getArtists()
    .then(function (artists) {
      self.artists = artists
    })
  }
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #19041995
  margin-top 60px

h1, h2
  font-weight normal

ul
  list-style-type none
  padding 0

li
  margin 10px

a
  color #42b983

.artists
  margin 0 auto
  width 800px
  max-width 100% 
  display flex
  flex-wrap wrap
  justify-content space-around

.artist
  padding 10px
.name
  margin-top 0

.photo img
  border-radius 50%
</style>
