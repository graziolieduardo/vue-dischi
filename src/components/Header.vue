<template>
  <div class="container-fluid">
      <div class="row h-100">
          <div class="col h-100 d-flex align-items-center">
              <img class="h-75 ps-3" src="../assets/img/logo.png" alt="logo">
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped lang="scss">
    @import '../assets/style/vars.scss';

    .container-fluid {
        height: 70px;
        background-color: $header-color;        
    }
</style>