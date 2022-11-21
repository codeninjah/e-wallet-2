<template>
  <div id="app">
      <nav>
        <a @click="currentView = 'home'"> HOME</a>
        <a @click="currentView = 'addCard'">ADD CARD</a>
      </nav>

      <ViewCards v-bind:cards="cardArray" v-if="currentView == 'home'"/>

      <ViewCards v-bind:cards="stored" v-if="currentView == 'home'"/>
      <AddCard @clicked="addToCardArray" v-else-if="currentView == 'addCard'"  />
      
  </div>
</template>

<script>
import AddCard from './views/AddCard.vue'
import ViewCards from './views/ViewCards.vue'

export default {
  name: 'App',
  components: {
    AddCard,
    ViewCards
  },

  data(){return{
    cardArray: [],
    currentView: 'home',
    storedData: [],
    stored: []
  }},

  methods: {
    addToCardArray(getItem){

      //compare if the cards number already exists in the array
      /*
      for(var i = 0; i < this.cardArray.length; i++){
        if(getItem.cardNumber == this.cardArray[i].cardNumber){
          alert("Number already exists")
        } 
      }
      */

      //Following wont work
      /*
      for(let card of this.cardArray){
        if(getItem.cardNumber !== card.cardNumber){
          alert("Works!")
          this.cardArray.push(getItem)
          this.storedData.push(getItem)
          console.log("Does this show up?")
        }
        
        if(getItem.cardNumber === card.cardNumber){
          alert("Card number already exists")
        }
      }
      */

        this.cardArray.push(getItem) 
        this.storedData.push(getItem) 

      localStorage.setItem("stored", JSON.stringify(this.storedData))

      if(localStorage){
        this.stored = JSON.parse(localStorage.getItem('stored'))
        console.log("Hej!")

        let test = Object.keys(this.stored)
        let test2 = Object.values(this.stored)
        console.log("Test is: " + test)
        console.log("Test2 is: " + test2)
        console.log("This.stored is: " + this.stored)
        
      }
      
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

a {
  margin-right: 50px;
  font-weight: 600;
}
</style>
