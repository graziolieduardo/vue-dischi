<template>
  <div class="container-fluid">
      <div class="row h-100 justify-content-between">
          <div class="col-2 h-100 d-flex align-items-center">
              <img class="h-75 ps-3" src="../assets/img/logo.png" alt="logo">
          </div>
          <div class="col-2 d-flex align-items-center">
              <form> 
                <label class="text-light" for="genre">Sort:</label>
                <select v-model="inputValue" 
                @change="$emit('emitGenre', inputValue)" 
                name="genre" id="genre">
                    <option value="">select a genre</option>
                    <option v-for="(genre, index) in allGenre" :key="index" :value="genre">{{ genre }}</option>
                </select>
              </form>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Header',
    props: ['allGenre'],
    data() {
        return {
            inputValue: ''
        }
    }
}
</script>

<style scoped lang="scss">
    @import '../assets/style/vars.scss';

    .container-fluid {
        height: 70px;
        background-color: $header-color;        
    }
</style>