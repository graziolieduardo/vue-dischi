<template>
  <div id="app">
    <Header
    @emitGenre="getGenre"
    @emitAuthor="getAuthor" 
    :allGenre="genreArray"
    :allAuthors="authorsArray"
    />
    <main>
      <Albums 
      @authorsArr="getArrAuthors"
      @genreArr="getArrGenre"
      :lastValue="selectValue"
      :lastAuthor="selectAuthor" 
      />
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
      selectAuthor: '',
      genreArray: [],
      authorsArray: []
    }
  },
  methods: {
    // metodi per input di generi 
    getGenre(value) {
      this.selectValue = value;
      console.log(this.selectValue);
    },
    getArrGenre(array) {
      this.genreArray = array;
    },
    // metodi per input author 
    getArrAuthors(array) {
      this.authorsArray = array;
    },
    getAuthor(value) {
      this.selectAuthor = value
;    }
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
