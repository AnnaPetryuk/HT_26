<template>
    <div id="app">
        <Store />
    </div>
</template>

<script>
    import Store from './components/Store.vue'

    export default {
        name: 'App',
        components: {
            Store
        },
        data() {
            return {
                foo: 123
            }
        }
    }
</script>

<style lang="scss">
    * {
        box-sizing: border-box;
    }
    .title {
        font-size: 40px;
        color: red;
    }
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
