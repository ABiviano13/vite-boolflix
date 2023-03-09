<script>
import store from '../store';

import { magnifyingGlassIcon } from '@heroicons/vue/24/outline';

export default {
    components: {
        magnifyingGlassIcon
    },
    data() {
        return{
            store,
            ocalSearch: ''
        }
    },
    methods: {
        setSearch() {
            this.store.valueInput = this.localSearch
        }
    }
}

</script>

<template>

    <header class="main-header">
        <div class="container">
            <img class="logo" src="../assets/netflix-new-logo.png" alt="logo netflix">
            <div class="input-search">
                <input type="text" class="search"
                    v-model= "localSearch"
                    @keyup.enter="setSearch"
                >
                <button class="button" @click="setSearch">
                    Search
                </button>
            </div>
        </div>
    </header>
  
</template>

<style lang='scss' scoped>
@use '../style/partials/variables' as *;
.main-header{
    background-color: $black;
    padding: 20px;

    .container{
        display: flex;
        align-items: center;
        justify-content: space-between;


        .search,
        .button{
            background-color: $black;
            color: $white;
            border: none;
            padding: 5px;
        }

        .search{
            border: 1px solid $white;
        }

        .logo{
            width: 10%;
        }
    }

}



</style>