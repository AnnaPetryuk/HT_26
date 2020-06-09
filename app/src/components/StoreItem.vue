<template>
    <div class="store-item">
        <ItemType 
            :styleForPercentSale="item.percentSale"
            :styleForTop="item.isTop"
            :styleForNew="item.isNew"
            :styleForSale="item.sale" />
    
        <div class="store-item__image">
            <img :src="item.img"/>
        </div>
        <h4 class="store-item__title">
            {{item.title}}
        </h4>
        <div class="store-item__price-before">
            {{priceBefore}}
            <span v-if="priceBefore">₴</span>
        </div>
        <div class="store-item__price-after">
            {{priceAfter}}
            <span>₴</span>
        </div>
    </div>
</template>

<script>
    import ItemType from './ItemType.vue'

    export default {
        name: 'StoreItem',
        components: {
            ItemType
        },
        props: {
            item: Object
        },
        computed: {
            priceBefore() {
                let price = '';

                if(this.item.percentSale || this.item.sale) {
                    price = this.item.price;
                }

                return price;
            },
            priceAfter() {
                let price = this.item.price;

                if(this.item.percentSale) {
                    price = this.item.price - (this.item.price * this.item.percentSale / 100);
                    price = Math.round(price);
                }
                if(this.item.sale) {
                    price = this.item.price - this.item.sale;
                }

                return price;
            }
        }
    }
</script>

<style scoped lang="scss">
    .store-item {
        position: relative;
        height: 350px;
        width: 250px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        padding: 15px;
        margin-bottom: 40px;
        transition: all 0.5s;

        &:hover {
            transform: scale(1.05);
            box-shadow: 0 0 5px 2px #000;
            cursor: pointer;
        }

        &__image {
            margin-top: 5px;
            height: 170px;
            display: flex;
            justify-content: center;
            align-items: center;

            img {
                width: 90%;
                height: auto;
            }
        }

        &__title {
            text-align: left;
            font-weight: normal;
        }

        &__price-before {
            height: 14px;
            font-size: 14px;
            margin: 5px 0;
            color: #a6a5a5;
            text-decoration: line-through;
        }

        &__price-after {
            height: 24px;
            font-size: 24px;
            margin: 5px 0;
            color: #f84147;
        }
    }
</style>
