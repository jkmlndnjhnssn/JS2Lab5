<template>
    <div>
        Lägg till kort i adressboken
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
        top: 0;
        height: 180px;
        width: 300px;
        background-color: rgba(224,142,121, 0.95);
        padding: 10px;
        margin: 20px;
        border-radius: 5px;
        text-align: center;
        color: white;
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
