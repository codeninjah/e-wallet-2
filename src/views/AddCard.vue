<template>
    <div class="wrapper">
        <h1>This is the AddCard vyn</h1>
        <Card :kort="kort" />
        <form  @submit.prevent="addCard">
            <p><input type="text" v-model="kort.cardNumber" placeholder="cardNumber" pattern="[0-9]{16}" title="Cardnumber may only contain numbers" maxlength="16" required></p>
            <p><input type="text" v-model="kort.cardHolder" placeholder="cardHolder" pattern="^[A-Za-z ]+$" title="Name may only contain letters" required></p>
            <div class="expiration">
            <select v-model="kort.expireMonth" id="month" name="month" required>
                <option value="00">-</option>
                <option value="01">01</option>
                <option value="02">02</option>
                <option value="03">03</option>
                <option value="04">04</option>
                <option value="05">05</option>
                <option value="06">06</option>
                <option value="07">07</option>
                <option value="08">08</option>
                <option value="09">09</option>
                <option value="10">10</option>
                <option value="11">11</option>
                <option value="12">12</option>
            </select>
             <select v-model="kort.expireYear" id="year" name="year" required>
                <option value="00">-</option>
                <option value="22">22</option>
                <option value="23">23</option>
                <option value="24">24</option>
                <option value="25">25</option>
                <option value="26">26</option>
            </select>
        </div>
        <p>
            <select v-model="kort.vendor" id="vendor" name="vendor" required>
                <option value="00">-</option>
                <option value="bitcoin">Bitcoin Inc.</option>
                <option value="blockchain">Blockchain</option>
                <option value="evil">Evil Corp</option>
                <option value="ninja">Ninja Bank</option>
            </select>
        </p>
        <p>
            <input v-model="kort.CCV" type="text" placeholder="CCV">
        </p>
        <button>ADD CARD</button>
        </form>
    </div>
</template>


<script>
import Card from '../components/Card.vue'

export default{
    components: {Card},
        data(){ return {
            kort : {
                vendor : '', 
                cardNumber : '', 
                cardHolder : '', 
                expireMonth : '', 
                expireYear : '', 
                CCV : ''
            }
        }
    },

    methods: {
        addCard(){
            let item = this.kort
            this.$emit('clicked', {...item})
            console.log("This.item is: " + this.item) //undefined
            console.log("This.kort is: " + this.kort) // [object Object]
            console.log("Child komponentens function funkar") //JA
        }
    },

}

</script>


<style scoped>

input{
    width: 400px;
    height: 40px;
    font-size: 20px;
    padding: 5px;
    border-radius: 5%;
    border: 2px solid black;
}

select {
    width: 410px;
    height: 40px;
    background-color: white;
    font-size: 20px;
    padding: 5px;
}

#month {
    width: 205px;
    height: 40px;
    background-color: white;
    font-size: 20px;
    padding: 5px;
}

#year {
    width: 205px;
    height: 40px;
    background-color: white;
    font-size: 20px;
    padding: 5px;
}

button {
    width: 410px;
    height: 40px;
    font-size: 20px;
    font-weight: 600;
    padding: 5px;
    background-color: white;
    border: 3px solid black;
}

button:hover {
    background-color: gray;
}

</style>