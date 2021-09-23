<template>
  <div class="container-fluid">
      <div class="row h-100 justify-content-between">
          <div class="col-2 h-100 d-flex align-items-center">
              <img class="h-75 ps-3" src="../assets/img/logo.png" alt="logo">
          </div>
          <div class="col-3 d-flex align-items-center">
              <form> 
                <label class="text-light pe-2" for="genre">Sort:</label>
                <!-- select genre  -->
                <select v-model="inputValue" 
                    @change="$emit('emitGenre', inputValue)" 
                    name="genre" id="genre">
                    <option value="">select a genre</option>
                    <option v-for="(genre, index) in allGenre" :key="index" :value="genre">{{ genre }}</option>
                </select>

                <!-- select author  -->
                <select
                    class="mx-3" 
                    v-model="authorValue" 
                    @change="$emit('emitAuthor', authorValue)" 
                    name="genre" id="genre">
                    <option value="">select an author</option>
                    <option v-for="(author, index) in allAuthors" :key="index" :value="author">{{ author }}</option>
                </select>
              </form>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Header',
    props: ['allGenre', 'allAuthors'],
    data() {
        return {
            inputValue: '',
            authorValue: ''
        }
    },
}
</script>

<style scoped lang="scss">
    @import '../assets/style/vars.scss';

    .container-fluid {
        height: 70px;
        background-color: $header-color;        
    }
</style>