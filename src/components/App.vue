<template>
  <div id="app">
    
    <div>
      <input-user v-on:add-card="addCard" />
    </div>

    <div>
      <address-card v-for="card in cardList" v-bind:marked="card" v-bind:key="card.id" v-on:test="markedFunction" v-on:update="update"
      v-bind:index="indexNr"/>
    </div>
      
    <div id="markedCard">
        {{markedName}}
        {{markedNr}}
    </div>

  </div>
</template>

<script>
import AddressCard from "./AddressCard.vue";
import InputUser from "./InputUser.vue";
export default {
  components: {
    "address-card": AddressCard,
    "input-user": InputUser,
  },
  data: function() {
    return {
      cardList: [],
        markedName : "",
        markedNr : undefined,
        indexNr : 0
    };
  },
  methods: {
    addCard: function(name, nr) {
      if(name !== "" && nr !== undefined) {
        let newCard = {
          name: name,
          nr: nr,
          indexNr : this.indexNr++
        };
          console.log(newCard);
        this.cardList.push(newCard);
      }
    },
    markedFunction : function(name, nr) {
        this.markedName = name;
        this.markedNr = nr;
    },
    update : function(name, nr, index) {
        console.log(name, nr, index);
    }
  }
};
</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
*{
  outline : none;
}
body {
  background-color : aqua;
}
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
    #markedCard{
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