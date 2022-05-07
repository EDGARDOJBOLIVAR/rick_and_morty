<template>
    <div class="filter">
        <div class="item" v-for="item in Filters" @click="filter(item.value)">{{item.name}}</div>
    </div>
</template>

<script>
import { useStore } from "vuex";

export default{
    setup(){
        const store = useStore();
        const Filters = [
            {name: 'All', value: ''},
            {name: 'Alive', value: 'Alive'},
            {name: 'Dead', value: 'Dead'},
            {name: 'Unknown', value: 'unknown'}
        ]

        const filter = ((status) =>{
            store.dispatch('filterByStatus', status)
        })
        return {
            filter,
            Filters
        }
    }

}
</script>

<style lang="scss">
.filter{
    width: 400px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    border-radius: 10px;
    overflow: hidden;
    .item{
        padding: 1rem 0.5rem;
        background-color: var(--background-card);
        text-align: center;
        cursor: pointer;
        &:hover{
            color: var(--text-orange);
        }
    }
}
</style>