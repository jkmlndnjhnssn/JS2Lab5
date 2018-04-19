<template>
    <div id = "card" v-on:click="$emit('test', marked.name, marked.nr, marked.adress)">
        <div v-if="normal">
           Namn: {{marked.name}}
        </div>
        <input v-if="editMode" type="text" placeholder='För- och Efternamn' v-model="newName">
        <div v-if="normal">
           Telefonnummer: {{marked.nr}}
        </div>
        <input v-if="editMode" type="text" placeholder='Telefonnummer' v-model="newNr">
        <div v-if="normal">
            Adress: {{marked.adress}}
        </div>
        <input v-if="editMode" type="text" placeholder='Adress' v-model="newAdress">
        <button v-if="normal" v-on:click="edit">Edit</button>
        <button v-if="editMode" v-on:click="update">Update</button>
    </div>
</template>

<script>
    export default {
        props: ['marked', 'index'],
        data: function() {
            return {
                editMode: false,
                normal: true,
                newName: undefined,
                newNr: undefined,
                newAdress: undefined
            }
        },
        methods: {
            edit: function() {
                if (!this.editMode) {
                    this.editMode = true;
                    this.normal = false;
                } else {
                    this.editMode = false;
                    this.normal = true;
                }

            },
            update: function() {
                if (!this.editMode) {
                    this.editMode = true;
                    this.normal = false;
                } else {
                    this.editMode = false;
                    this.normal = true;
                }
                this.$emit('update', this.newName, this.newNr, this.newAdress, this.index);
            }
        }
    }

</script>

<style scoped>
    #card {
        position: relative;
        top: 10px;
        width: 350px;
        height: 160px;
        background-color: #E08E79;
        margin: auto;
        text-align: center;
        margin-top: 10px;
        color: white;
        padding: 10px;
        border-radius: 5px;
    }

    input,
    button {
        flex: 1 1 auto;
        margin-top: 10px;
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
        margin-bottom: 10px;
        background-color: #774F38;
        color: white;
        font-size: 1.2em;
    }

    div, input {
        background-color: white;
        color: black;
        margin: auto;
        margin-top: 5px;
        width: 60%;
        border-radius: 5px;
        text-align: left;
        padding: 5px;
    }

</style>
