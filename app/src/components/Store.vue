<template>
    <div id="store">
        <div v-for="item in goods" v-bind:key="item.id">
            <store-item :item="item"></store-item>
        </div>
    </div>
</template>

<script>    
    import axios from 'axios'
    import StoreItem from './StoreItem.vue'

    export default {
        name: 'Store',
        components: {
            StoreItem
        },
        data() {
            return {
                goods: null
            }
        },
        mounted() {
            axios
                .get('http://localhost:3003/getGoods/')
                .then(response => (this.goods = response.data))
                .catch(error => console.log(error));
        }
    }
</script>

<style lang="scss">
    #store {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        margin: 20px;
    }
</style>
