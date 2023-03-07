<script>
import axios from 'axios'

export default {

    data() {
        return {
            filmArray: []
        }
    },
    methods: {
        fechFilm() {
            axios
                .get('https://api.themoviedb.org/3/search/movie?api_key=9feb0690aacb6d5cd46a246f69bb9918&query=ironman')
                .then((response) => {
                    console.log(response)
                    this.filmArray = response.data.results
                    console.log(this.filmArray)
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
                <li class="card"
                v-for="cardFilm in filmArray"
                > 
                    <h2 class="title-film">
                        {{ cardFilm.title }}
                    </h2>
                    <h3 class="title-original-film">
                        {{ cardFilm.original_title }}
                    </h3>
                    <div class="description-film">
                        {{ cardFilm.overview }}
                    </div>
                </li>
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
    }
}

</style>