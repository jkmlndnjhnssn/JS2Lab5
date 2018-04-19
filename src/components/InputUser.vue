<template>
    <div>
        <input type="text" placeholder="För- och Efternamn" v-model="name" />
        <input type="text" placeholder="Telefonnummer" v-model="nr" />
        <input type="text" placeholder="Adress" v-model="adress" />
        <button v-on:click="$emit('add-card', name, nr, adress)">Lägg till kort</button>
    </div>
</template>

<script>
    export default {
        data: function() {
            return {
                name: '',
                nr: undefined,
                adress: ''
            }
        }
    }

</script>

<style scoped>
    div {
        position: fixed;
        display: flex;
        flex-direction: column;
        top: 0;
        height: 160px;
        width: 300px;
        background-color: #E08E79;
        padding: 10px;
        margin: 20px;
        border-radius: 5px;
    }
    
    input {
        margin: auto;
        width: 60%;
    }

    input,
    button {
        flex: 1 1 auto;
        margin-top: 5px;
        border: none;
        border-radius: 5px;
        padding: 5px;
    }

    button {
        position: relative;
        text-align: center;
        margin-bottom: 10px;
        width: 150px;
        margin: auto;
        margin-top: 10px;
        background-color: #774F38;
        color: white;
        font-size: 1.2em;
    }

</style>
