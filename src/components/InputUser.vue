
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
*{
    text-align: left;
}
div{
    position: absolute;
    top: 0;
    width: 100px;
}
</style>