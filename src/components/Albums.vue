<template>
    <div class="container-fluid p-5 w-75 h-100">
        <div class="row w-100 flex-wrap">
            <Album 
            v-for="(album, index) in filteredAlbums" 
            :key="index"
            :item="album"
            />
        </div>
    </div>
</template>

<script>
import Album from './Album.vue'
import axios from 'axios'

export default {
    name: 'Albums',
    props: ['lastValue'],
    data() {
        return {
            myApi: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            genreArray: []
        }
    },
    methods: {
        getAlbums() {
            axios
                .get(this.myApi)
                .then(res => {
                    this.albums = res.data.response;
                    // console.log(this.albums);
                })
        },
        getGenre() {
            axios
                .get(this.myApi)
                .then(res => {
                    let array = res.data.response;
                    for (let i = 0; i < array.length; i++) {
                        if (!this.genreArray.includes(array[i].genre)) {
                            this.genreArray.push(array[i].genre)
                        } 
                    }
                })
                this.$emit('genreArr', this.genreArray);
        }
    },
    computed: {
        filteredAlbums() {
            console.log(this.albums)
            if (this.lastValue == '') {
                return this.albums
            } else {
                const filteredArray = this.albums.filter((element) => {
                    if(element.genre == this.lastValue) {
                        return element;
                    } 
                });
                return filteredArray;
            }
        },
    },
    created() {
        this.getAlbums();
        this.getGenre();
    },
    components: {
        Album
    }
}
</script>

<style scoped lang="scss">

</style>