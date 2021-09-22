<template>
  <div class="album-box col-2 m-3">
      <img class="img-fluid" :src="item.poster" :alt="item.title">
      <h3>{{ item.title }}</h3>
      <div>
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
            width: 100%;
        }
    }
</style>