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
        },
        overview: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            flags: {
                it: 'it.png',
                en: 'en.png',
                hi:'india.png',
                ja:'japan.png',
                ko: 'korea.png',
                fr: 'france.png'
            }
        }
    },
    methods: {
        // setLanguageIcon() {
        //     const languageIcon = 'https://flagcdn.com/w20/' + this.language + '.png'
        //     // console.log(languageIcon)
        //     return languageIcon

        // },
        setCover() {
            const URL = 'https://image.tmdb.org/t/p/' + 'w342' + this.urlFinal
            return URL
        },
        setVote() {
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
    <img 
        class="cover"
        :src="setCover()" alt=""
    >
    <div class="description">

        <div class="title flex">
            <h4>
                Titolo:
            </h4>
            <div>
                {{ title }}
            </div>
        </div>

        <div class="title-original flex" 
        v-if= " titleOriginal !== title ">
            <h4>
                Titolo Originale:
            </h4>
            <div>
                {{ titleOriginal }}
            </div>
        </div>

        <div class="language flex">

            <h4>
                Lingua:
            </h4>
            <img
                v-if="flags[language]"
                :src= "flags[language]"
                width="25"
                :alt="language"
            >
            <p v-else>
                {{ language }}
            </p>
        </div>
        <div class="vote-star flex">

            <h4>
                Voto:
            </h4>
            <StarIcon 
                class="star"
                v-for="star in setVote() "
            ></StarIcon>
            <StarIconOutline 
                class="star"
                v-for="star in (5 - setVote())"
            ></StarIconOutline>

        </div>
        <div class="overview flex">
            <h4>
                Descrizione:
            </h4>
            {{ overview }}
        </div>
    </div>
</li>

</template>

<style lang="scss" scoped>
@use '../style/partials/variables' as *;
.card{
    position: relative;

    &:hover {
        
        .description{
            display: flex;
        }
    }

    .cover{
        height: 100%;
    }

    
    .description {
        background-color: $blackhover;
        width: 100%;
        height: 100%;
        font-size: 13px;
        color: $white;
        padding-top: 20px;
        display: none;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        flex-direction: column;
        justify-content: center;
        padding: 20px;
        overflow: scroll;


        .flex{
            display: flex;
            gap: 5px;
        }

        .star{
            width: 10px;
        }

        .overview{
            font-size: 10px;
        }

        .display-none{
            display: none;
        }
    }
}


</style>