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
    props: ['lastValue', 'lastAuthor'],
    data() {
        return {
            myApi: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            genreArray: [],
            authorsArray: []
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
            for (let i = 0; i < this.albums.length; i++) {
                if (!this.genreArray.includes(this.albums[i].genre)) {
                    this.genreArray.push(this.albums[i].genre)
                } 
            }
            this.$emit('genreArr', this.genreArray);

            // prova con axios
            // axios
            //     .get(this.myApi)
            //     .then(res => {
            //         let array = res.data.response;
            //         for (let i = 0; i < array.length; i++) {
            //             if (!this.genreArray.includes(array[i].genre)) {
            //                 this.genreArray.push(array[i].genre)
            //             } 
            //         }
            //     })
            // this.$emit('genreArr', this.genreArray);
        },
        getAuthors() {
            for (let i = 0; i < this.albums.length; i++) {
                if (!this.authorsArray.includes(this.albums[i].author)) {
                    this.authorsArray.push(this.albums[i].author)
                } 
            }
            this.$emit('authorsArr', this.authorsArray);
        }
    },
    computed: {
        filteredAlbums() {
            // console.log(this.albums)
            if ((this.lastValue == '') && (this.lastAuthor == '')) {
                return this.albums
            } 
            else if ((this.lastValue != '') && (this.lastAuthor == '')){
                const filteredArray = this.albums.filter((element) => {
                    if(element.genre == this.lastValue) {
                        return element;
                    } 
                });
                return filteredArray;
            } 
            else if ((this.lastValue == '') && (this.lastAuthor != '')) {
                const filteredArray = this.albums.filter((element) => {
                    if(element.author == this.lastAuthor) {
                        return element;
                    } 
                });
                return filteredArray;
            } 
            else {
                const filteredArray = this.albums.filter((element) => {
                    if((element.author == this.lastAuthor) && (element.genre == this.lastValue)) {
                        return element;
                    } 
                });
                return filteredArray;
            }
        }
    },
    created() {
        this.getAlbums();
    },
    beforeUpdate () {
        this.getGenre();
        this.getAuthors();
    },
    components: {
        Album
    }
}
</script>

<style scoped lang="scss">

</style>