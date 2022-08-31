<template>
    <div class="container">
        <input v-model="inputSearch" type="text"/>
        <button @click="$emit('effettuaRicerca', inputSearch)">Cerca</button>
    </div>
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

<style>

</style>