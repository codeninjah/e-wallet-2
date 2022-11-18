<template>
    <div class="wrapper">
        <h1>This is the ViewCards view</h1>
        <div class="active">
            <Card v-bind:kort="loopCards[this.position]" />
        </div>
        <ul class="cards-list">
            <Card 
            v-for="(card, index) in loopCards"
            :key="index"
            v-bind:kort="card"
            :card = "loopCards[index]"
            @active="active(index)"/>
        </ul>
        <button @click="deleteCard(position)">Remove</button>
    </div>
</template>


<script>
import Card from '../components/Card.vue'

    export default {

        components: {Card},

        props: ['cards', 'index'],

        data(){return{
            position: null
        }},

        methods: {
            active(index){
                console.log("Index is: " + index)
                this.position = index
                console.log("Position is: " + this.position)
            },
            deleteCard(index){
                let lsData = JSON.parse(localStorage.getItem('stored'))
                this.cards.splice(index)
                console.log("This is in localStorage before splice: " + lsData)

                let confirmDelete = confirm("Are you sure you want to delete this?")

                if(confirmDelete){
                    lsData.splice(index)
                    localStorage.setItem('stored', JSON.stringify(lsData))
                    console.log("Remove at: " + index)
                    //lsData.splice(index)
                    console.log("This is in localStorage after splice: " + lsData)

                    if(lsData.length == 0){
                        localStorage.removeItem('stored')
                    }
                }       
                

            }
        },
        computed: {
            loopCards(){
                console.log("Loop CARDS!")
                return this.cards
            }
        }
    }
</script>


<style scoped>

ul {
    list-style-type: none;
}

.active {
    padding-left: 40px;
}



</style>
