<template>
        <div class="wrapper" 
            v-bind:class="kort.vendor" 
            v-on:click="$emit('active')">
            <div class="logo">
                <p v-if="kort.vendor == ''"> <img src="../assets/ninja.svg"></p>
                <p v-if="kort.vendor == 'evil'"><img src="../assets/evil.svg"></p>
                <p v-else-if="kort.vendor == 'bitcoin'"><img src="../assets/bitcoin.svg"></p>
                <p v-else-if="kort.vendor == 'ninja'"><img src="../assets/ninja.svg"></p>
                <p v-else-if="kort.vendor == 'blockchain'"><img src="../assets/blockchain.svg"></p>
            </div>
            <div class="wifi">
                <p v-if="kort.vendor !== 'bitcoin'"><img src="../assets/wifi_white.svg"></p>
                <p v-else><img src="../assets/wifi.svg"></p>
            </div>
            <div class="chip">
                <p><img src="../assets/chip.svg"></p>
            </div>
            <p class="card-nr">{{spacedCardNumbers}}</p>
            <div class="name-expire">
                <div class="card-text">
                    <div>CARDHOLDERS NAME</div>
                    <div>VALID UNTIL</div>
                </div>
                <div class="card-info">
                    <div>{{kort.cardHolder}}</div>
                    <div>{{kort.expireMonth}}/{{kort.expireYear}}</div>
                </div>
            </div>
        </div>   
</template>



<script>
    export default {
        props: ['kort', 'index'],

        computed : {
        spacedCardNumbers(){
            let newNumbers = '';

            for(let i = 0; i < this.kort.cardNumber.length; i++){
                if(i % 4 == 0){
                    newNumbers += ' ';
                }

                newNumbers += this.kort.cardNumber[i]

                if(newNumbers.length > 20){
                    return newNumbers
                }

            }

            return newNumbers
        }
    }
    }
</script>


<style scoped>

.wrapper{
    height: 450px;
    border: 1px solid black;
    border-radius: 5%;
    margin-left: auto;
    margin-right: auto;
    width: 40%;
    background-color: gray;
    color: white;
}

.evil {
    background-color: red;
    color: white;
}

.bitcoin {
    background-color: orange;
    color: white;
}

.blockchain {
    background-color: purple;
    color: white;
}

.ninja {
    background-color: black;
    color: white;
}

.name-expire {
    display: grid;
}
    
.card-text {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-right: 20px;
    margin-left: 20px;
    font-size: 20px;
}

.card-info {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-right: 20px;
    margin-left: 20px;
    font-size: 26px;
}

.card-nr {
    font-size: 52px;
    max-height: 60px;
}

.logo{
    text-align: right;
    padding: 10px;
    max-height: 40px;
}

.wifi{
    text-align: left;
    padding: 10px;
    max-height: 40px;
}

.chip{
    text-align: left;
    padding: 10px;
    max-height: 40px;
}

img {
    width: 80px;
    height: 80px;
}

.logo > img {
    width: 100px;
    height: 100px;
}



</style>
