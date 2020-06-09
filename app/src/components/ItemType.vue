<template>
    <div class="item-type">
        <div class="item-type__remark"
            v-if="current" 
            v-bind:style="{background: current.background}">
            {{current.text}}
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ItemType',
        props: {
            styleForPercentSale: Number,
            styleForTop: Boolean,
            styleForNew: Boolean,
            styleForSale: Number
        },
        data() {
            return {
                styles: [
                    {
                        value: this.styleForTop,
                        background: '#ffa900',
                        text: 'Топ продаж'
                    },
                    {
                        value: this.styleForNew,
                        background: '#712bd4',
                        text: 'Новинка'
                    },
                    {
                        value: this.styleForSale,
                        background: '#f84147',
                        text: 'Акция'
                    },
                    {
                        value: this.styleForPercentSale,
                        background: '#f84147',
                        text: this.styleForPercentSale + '%'
                    }
                ]
            }
        },
        computed: {
            current() {
                let value = null;
                
                this.styles.forEach(function(item) {
                    if(item.value) {
                        value = item;
                    }
                });
                
                return value;
            }
        }
    }
</script>

<style lang="scss">
    .item-type {
        height: 24px;
        
        &__remark {
            border-radius: 15px;
            padding: 0 8px;
            line-height: 24px;
            font-size: 12px;
            font-weight: bold;
            color: white;
            text-transform: uppercase;
        }
    }
</style>
