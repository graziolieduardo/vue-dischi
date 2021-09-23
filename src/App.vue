<template>
  <div id="app">
    <Header
    @emitGenre="getGenre" 
    :allGenre="genreArray"
    />
    <main>
      <Albums 
      @genreArr="getArrGenre"
      :lastValue="selectValue" />
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Albums from './components/Albums.vue'

export default {
  name: 'App',
  components: {
    Header,
    Albums
  },
  data() {
    return {
      selectValue: '',
      genreArray: []
    }
  },
  methods: {
    getGenre(value) {
      this.selectValue = value;
      console.log(this.selectValue);
    },
    getArrGenre(array) {
      this.genreArray = array;
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general.scss';
  @import './assets/style/vars.scss';

main {
  height: calc(100vh - 70px);
  background-color: $main-color;
}
</style>
