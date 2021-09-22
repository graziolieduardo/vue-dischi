<template>
    <div class="wrapper">
        <div class="container-fluid pt-5 w-75">
            <div class="row">
                <Album 
                v-for="(album, index) in albums" 
                :key="index"
                :item="album"
                />
            </div>
        </div>
    </div>
</template>

<script>
import Album from './Album.vue'
import axios from 'axios'

export default {
    name: 'Albums',
    data() {
        return {
            myApi: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: []
        }
    },
    methods: {
        getAlbums() {
            axios
                .get(this.myApi)
                .then(res => {
                    this.albums = res.data.response;
                    console.log(this.albums);
                })
        }   
    },
    created() {
        this.getAlbums();
    },
    components: {
        Album
    }
}
</script>

<style scoped lang="scss">
    @import '../assets/style/vars.scss';

    .wrapper {
        height: calc(100vh - 70px);
        background-color: $main-color;
    }
</style>