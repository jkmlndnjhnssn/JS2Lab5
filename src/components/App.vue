<template>
  <div id="app">

    <div>
      <input-user v-on:add-card="addCard" />
    </div>

    <div>
      <address-card v-for="(card, index) in cardList" v-bind:marked="card" v-bind:index="index" v-bind:key="card.id" v-on:test="markedFunction" v-on:update="update"/>
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
        markedNr : undefined
    };
  },
  methods: {
    addCard: function(name, nr) {
      if(name !== "" && nr !== undefined) {
        let newCard = {
          name: name,
          nr: nr
        };
        this.cardList.push(newCard);
      }
    },
    markedFunction : function(name, nr) {
        this.markedName = name;
        this.markedNr = nr;
    },
    update : function(namePara, nrPara, indexPara) {
      let updatedCard = {
        name : namePara,
        nr : nrPara
      }
      this.markedName = updatedCard.name;
      this.markedNr = updatedCard.nr;
      this.cardList.splice(indexPara, 1, updatedCard);
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
  background-color : blue;
}
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
    #markedCard{
        position: absolute;
        top: 0;
        right: 0;
        width: 300px;
        height: 250px;
        background-color: red;
        color: white;
        text-align: center;
        margin: 20px;
    }
</style>
