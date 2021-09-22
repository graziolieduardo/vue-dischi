<template>
  <div class="album-box col-2 my-2 mx-3 d-flex flex-column align-items-center py-2">
      <img class="img-fluid w-75" :src="item.poster" :alt="item.title">
      <h3 class="text-center p-3 text-uppercase">{{ item.title }}</h3>
      <div class="d-flex flex-column align-items-center">
          <div>{{ item.author }}</div>
          <div>{{ item.year }}</div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Album',
    props: ['item']
}
</script>

<style scoped lang="scss">
    @import '../assets/style/vars.scss';

    .album-box {
        background-color: $header-color;
        color: #fff;

        img {
            aspect-ratio: 1/1;
        }

        div {
            color: $text-color;
        }
    }
</style>