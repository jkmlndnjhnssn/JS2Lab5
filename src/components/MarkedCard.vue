
<template>
    <div id="markedDiv" v-on:test="printMarked">
    </div>
</template>

<script>
export default {
    props : {
        marked : undefined
    },
    data : function() {
        return {
            name : "",
            nr : ""
        }
    },
    methods : {
        printMarked : function(name, nr) {
            console.log("Test");
        }
    }
}
</script>

<style scoped>
#markedDiv {
    position: absolute;
    top: 0;
    right: 0;
    width: 100px;
    height: 100px;
    background-color: red;
    color: white;
    text-align: center;
}
</style>
