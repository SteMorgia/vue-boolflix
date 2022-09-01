<template>
    <header>
        <div class="containerLogo">
            <img src="../assets/boolflixLogo/logo.png" alt="">
        </div>
        <div class="containerSearch">
            <input v-model="inputSearch" type="text"/>
            <button @click="$emit('effettuaRicerca', inputSearch)">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name:'MyHeader',
    data() {
        return {
            inputSearch: ''
        }
    },
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        height: 100px;
        background-color: #000;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;
        .containerSearch {
            margin-right:10px;
        }
    }
</style>