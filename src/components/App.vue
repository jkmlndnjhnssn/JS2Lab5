<template>
  <div id="app">

    <div>
      <input-user v-on:add-card="addCard" />
    </div>

    <div>
      <address-card v-for="(card, index) in cardList" v-bind:marked="card" v-bind:index="index" v-bind:key="card.id" v-on:test="markedFunction" v-on:update="update"/>
    </div>

    <div id="markedCard">
        <span>
            Markerat adresskort
        </span>
        <div>{{markedName}}</div>
        <div>{{markedNr}}</div>
        <div>{{markedAdress}}</div>
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
        markedAdress: ""
    };
  },
  methods: {
    addCard: function(name, nr, adress) {
      if(name !== "" && nr !== undefined && adress !== "") {
        let newCard = {
          name: name,
          nr: nr,
          adress: adress
        };
          console.log(newCard);
        this.cardList.push(newCard);
      }
    },
    markedFunction : function(name, nr, adress) {
        this.markedName = name;
        this.markedNr = nr;
        this.markedAdress = adress;
    },
    update : function(namePara, nrPara, adressPara, indexPara) {
      let updatedCard = {
        name : namePara,
        nr : nrPara,
        adress : adressPara
      }
      this.markedName = updatedCard.name;
      this.markedNr = updatedCard.nr;
      this.markedAdress = updatedCard.adress;
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
  background-color : #ECE5CE;
}
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
    #markedCard{
        position: fixed;
        top: 0;
        right: 0;
        width: 300px;
        height: 160px;
        background-color: #E08E79;
        color: white;
        text-align: center;
        margin: 20px;
        border-radius: 5px;
        padding:10px;
    }
    #markedCard > div {
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
