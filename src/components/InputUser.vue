
<template>
    <div>
        <input type="text" placeholder="Name" v-model="name" />
        <input type="text" placeholder="Nr" v-model="nr" />
        <button v-on:click="$emit('add-card', name, nr)">Add Card</button>
    </div>
</template>

<script>
export default {
    data : function() {
        return {
            name : '',
            nr : undefined
        }
    }
}
</script>

<style scoped>
div{
    position: absolute;
    display: flex;
    flex-direction: column;
    top: 0;
    background-color: red;
    padding: 20px;
    margin: 20px;
}
input, button{
    flex: 1 1 auto;
    margin-top: 10px;
}
button{
    position: relative;
    text-align: center;
    margin-bottom: 10px;
    width: 50%;
    margin: auto;
    margin-top: 10px;
    margin-bottom: 10px;
    background-color: white;
    border: solid black 1px;
    font-size: 1.2em;
}
</style>
