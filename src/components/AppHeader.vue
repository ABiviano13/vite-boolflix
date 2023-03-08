<script>
import store from '../store';

export default {
  data() {
    return{
        store
    }
  }
}

</script>

<template>

    <header class="main-header">
        <div class="container">
            <input type="text" class="input-search"
            v-model= "store.valueInput"
            >
            <button class="button">
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