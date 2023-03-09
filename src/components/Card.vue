<script>
import { StarIcon } from '@heroicons/vue/24/solid'
import { StarIcon as StarIconOutline } from '@heroicons/vue/24/outline'
export default {
    components: {
        StarIcon,
        StarIconOutline
    },
    props: {
        title: {
            type: String,
            required: true
        },
        titleOriginal: {
            type: String,
            required: true
        },
        language: {
            type: String,
            required: true
        },
        vote: {
            type: Number,
            required: true
        },
        urlFinal: {
            type: String,
            required: true
        }
    },
    methods: {
        fechLanguageIcon() {
            const languageIcon = 'https://flagcdn.com/w20/' + this.language + '.png'
            // console.log(languageIcon)
            return languageIcon

        },
        fechCover() {
            const URL = 'https://image.tmdb.org/t/p/' + 'w342' + this.urlFinal
            return URL
        },
        fechVote() {
            // const voteInt = Math.round(this.vote)
            const voteInt = this.getVote(this.vote)
            console.log(vote)
            return voteInt
        },
        getVote(vot) {
            const min = Math.ceil(1);
            const max = Math.floor(5);
            const vot = Math.floor((1 - 5) + 5); 
            return vot
        }
    }
    
}

</script>

<template>

<li class="card"> 
    <img :src="fechCover()" alt="">
    <h2 class="title-film">
        {{ title }}
    </h2>
    <h3 class="title-original-film">
        {{ titleOriginal }}
    </h3>
    <div class="description-film">
        <div class="language-vote">
            <img
                :src= "fechLanguageIcon()"
                width="20"
                :alt="language"
            >
           {{fechVote()}}
           <StarIcon class="star"></StarIcon>
           <StarIconOutline class="star"></StarIconOutline>
        
        </div>
    </div>
</li>

</template>

<style lang="scss" scoped>

.description-film {
    font-size: 13px;
    padding-top: 10px;

    .language-vote{
        padding-top: 5px;
        font-weight: bold;

        .star{
            width: 10px;
        }
    }
}

</style>