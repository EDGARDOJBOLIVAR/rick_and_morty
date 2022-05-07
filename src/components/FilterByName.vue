<template>
    <div class="search">
        <input type="text" placeholder="Buscar por nombre" @keyup="filter()" v-model="name">
    </div>
</template>

<script>
import { ref } from "vue";
import { useStore } from "vuex";

export default {
    setup(){
        const store = useStore();
        const name = ref('');

        const filter = () =>{
            store.dispatch('filterByName', name.value);
        }

        return {
            filter, name
        }
    }
}
</script>

<style lang="scss">
.search{
    width: 450px;
    margin: auto;
    input{
        height: 53px;
        width: 400px;
        border: none;
        border-radius: 10px;
        padding: 0 0.5rem;
    }
}
</style>