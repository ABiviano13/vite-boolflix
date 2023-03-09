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
            const div = this.vote % 2 
            const voteInt = Math.round(div)
            // console.log(voteInt)
            return voteInt
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
           {{ fechVote() }}
           <StarIcon 
           class="star"
           v-for="star in fechVote() "
           v-if="fechVote() !== 0"
           ></StarIcon>
           <StarIconOutline 
           class="star"
           v-for="star in (5 - fechVote())"></StarIconOutline>
        
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

        .display-none{
            display: none;
        }
    }
}

</style>