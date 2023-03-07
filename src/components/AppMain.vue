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
            // filmArray: []
            store
        }
    },
    methods: {
        fechFilm() {
            axios
                .get('https://api.themoviedb.org/3/search/movie?api_key=9feb0690aacb6d5cd46a246f69bb9918&query=ironman')
                .then((response) => {
                    console.log(response)
                    this.store.filmArray = response.data.results
                    // console.log(this.filmArray)
                })
        }
    },
    created() {
        this.fechFilm()
    }

  
}
</script>

<template>

    <main class="main-content">
        <div class="container">
            <ul class="list-card">
                <Card
                v-for="cardFilm in store.filmArray"
                :title="cardFilm.title"
                :titleOriginal="cardFilm.original_title"
                :description="cardFilm.overview"
                :language="cardFilm.original_language"
                :vote="cardFilm.vote_average"
                ></Card>
            </ul>
        </div>
    </main>
  
</template>

<style lang="scss">

.main-content{
    background-color: gray;
    height: 100vh;

    .list-card{
        display: grid;
        grid-template-columns: repeat(2,1fr);
        gap: 15px;

        .description-film {
            font-size: 13px;
        }
    }
}

</style>