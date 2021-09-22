<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col">
                <Album />
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
</style>