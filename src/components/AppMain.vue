<script>
import axios from 'axios'

import store from '../store'

import Card from './Card.vue'

export default {
    components: {
        Card
    },
    data() {
        return {
            store
        }
    },
    methods: {
        fechFilm() {
            axios
                .get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key:'9feb0690aacb6d5cd46a246f69bb9918',
                        query: this.valueInput,
                    }
                })
                .then((response) => {
                    // console.log('film',response)
                    this.store.filmArray = response.data.results
                    // console.log(this.filmArray)
                })
                .catch(err => {
                    this.store.filmArray = []
                })
        },
        fechtv() {
            axios
                .get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        api_key:'9feb0690aacb6d5cd46a246f69bb9918',
                        query: this.valueInput
                    }
                })
                .then((response) => {
                    // console.log('serie tv', response)
                    this.store.tvArray = response.data.results
                    // console.log(this.tvArray)
                })
                .catch(err => {
                    this.store.tvArray = []
                })
        }
    },
    created() {
        this.fechFilm(),
        this.fechtv()
    },
    computed: {
        filmArray() {
            return store.filmArray
        },
        tvArray() {
            return store.tvArray
        },
        valueInput() {
            return store.valueInput
        }
    },
    watch: {
        valueInput(newVal, oldVal) {
            this.fechFilm()
            this.fechtv()
        }
    }

  
}
</script>

<template>

    <main class="main-content">
        <div class="container">
            
            <ul class="list-card">
                <Card
                v-for="cardFilm in filmArray"
                :title="cardFilm.title"
                :titleOriginal="cardFilm.original_title"
                :language="cardFilm.original_language"
                :vote="cardFilm.vote_average"
                :urlFinal="cardFilm.poster_path"
                :overview="cardFilm.overview"
                ></Card>
            </ul>

            <ul class="list-card">
                <Card
                v-for="cardTv in tvArray"
                :title="cardTv.name"
                :titleOriginal="cardTv.original_name"
                :language="cardTv.original_language"
                :vote="cardTv.vote_average"
                :urlFinal="cardTv.poster_path"
                :overview="cardTv.overview"
                ></Card>
            </ul>

        </div>
    </main>
  
</template>

<style lang="scss">
@use '../style/partials/variables' as *;

.main-content{
    background-color: $black;
    height: 100vh;
    overflow: scroll;

    .list-card{
        display: flex;
        overflow-x: scroll;
        overflow-y: hidden;
    }
}

</style>