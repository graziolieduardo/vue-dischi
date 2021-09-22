<template>
  <div class="container-fluid">
      <div class="row">
          <div class="col">
              <img src="../assets/img/logo.png" alt="logo">
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

        .row {
            height: 100%;

            .col {
                display: flex;
                align-items: center;
                height: 100%;

                img {
                    height: 80%;
                    padding-left: 20px;
                }
            }
        }
    }
</style>