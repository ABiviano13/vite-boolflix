<script>
import store from '../store';

export default {
  data() {
    return{
        store,
        localSearch: ''
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
            <input type="text" class="input-search"
            v-model= "localSearch"
            @keyup.enter="setSearch"
            >
            <button class="button" @click="setSearch">
                Ricerca
            </button>
        </div>
    </header>
  
</template>

<style scoped>
.main-header{
    background-color: black;
    padding: 20px;
}

</style>