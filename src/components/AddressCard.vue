
<template>
    <div id = "card" v-on:click="$emit('test', marked.name, marked.nr)">
        <div>
            {{marked.name}}
        </div>
        <div>
            {{marked.nr}}
        </div>
    </div>
</template>

<script>
export default {
    props :   ['marked'],
    
    data : function() {
        return {
            name : "",
            nr : ""
        }
    },
    methods : {
    }
}
</script>

<style scoped>
#card{
    width: 250px;
    height: 100px;
    background-color: red;
    margin: auto;
    text-align: center;
    margin-top: 10px;
    border-radius: 10px;
    color: white;
}
</style>