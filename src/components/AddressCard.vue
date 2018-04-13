
<template>
    <div id = "card" v-on:click="$emit('test', marked.name, marked.nr)">
        <div v-if="normal">
            {{marked.name}}
        </div>
        <input v-if="editMode" type="text" placeholder='name' v-model="newName">
        <div v-if="normal">
            {{marked.nr}}
        </div>
        <input v-if="editMode" type="text" placeholder='number' v-model="newNr">
        <button v-if="normal" v-on:click="edit">Edit</button>
        <button v-if="editMode" v-on:click="update">Update</button>
    </div>
</template>

<script>
export default {
    props :   ['marked', 'index'],
    
    data : function() {
        return {
            editMode : false,
            normal : true,
            newName : undefined,
            newNr : undefined
        }
    },
    methods : {
        edit : function() {
            if(!this.editMode) {
                this.editMode = true;
                this.normal = false;
            }
            else {                                
                this.editMode = false;
                this.normal = true;   
            }
            
        },
        update : function() {
            if(!this.editMode) {
                this.editMode = true;
                this.normal = false;
            }
            else {                                
                this.editMode = false;
                this.normal = true;   
            }
            this.$emit('update', this.newName, this.newNr, this.index);
        }
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