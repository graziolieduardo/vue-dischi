<template>
  <div class="album-box d-flex flex-column align-items-center p-4">
      <img class="img-fluid w-75" :src="item.poster" :alt="item.title">
      <h3 class="text-center text-uppercase py-3">{{ item.title }}</h3>
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

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .album-box {
        background-color: $header-color;
        color: #fff;
        width: calc((100% / 5) - 30px);
        height: 350px;
        margin: 15px;

        img {
            aspect-ratio: 1/1;
        }

        h3 {
            font-size: 20px;
        }

        div {
            color: $text-color;
        }
    }
</style>