<script>
export default {
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
            type: String,
            required: true
        }
    },
    methods: {
        fechLanguageIcon(language) {
            const languageIcon = 'https://flagcdn.com/w20/' + language + '.png'
            console.log(languageIcon)
            return languageIcon

        }
    }
    
}

</script>

<template>

<li class="card"> 
    <h2 class="title-film">
        {{ title }}
    </h2>
    <h3 class="title-original-film">
        {{ titleOriginal }}
    </h3>
    <div class="description-film">
        <div class="language-vote">
            <img
                :src= "fechLanguageIcon(language)"
                width="20"
                :alt="language">
        {{ vote }}
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
    }
}

.display-none{
    display: none;
}

</style>