<template>
  <div >

      <div class="c" v-for="x in data_dice" v-bind:key="x">
        <img class="dice" width="100" height="100" :src="require(`./assets/dice_/Dice_${x.nDice}.svg`)"/>
      </div>
    <div class="f">
        <div class="x-col">

        </div>
        <div class="x-col">
           <button @click="addDice()">Add Dice</button>
           <button @click="roolDice()">Rool Dice</button>
           <button @click="removeDice()">Remove Dice</button>
        </div>
         <div class="x-col d">
           Total angka Dadu : {{Number(total_dice)}}
           <br>
           <br>
           Total Dadu : {{Number(data_dice.length)}}
        </div>
    </div>
  </div>
</template>

<script>
export default {
  data:()=>{
    return{
      data_dice:[],
      total_dice:0
    }
  },
  methods: {
    addDice(){
      this.data_dice.push({
        nDice:Math.floor(Math.random() * 6 ) + 1
      })
      console.log(this.data_dice)
    },
    roolDice(){
      for(let i in this.data_dice){
        let ranD = Math.floor(Math.random() * 6 ) + 1
        this.data_dice[i].nDice = ranD
      }
      this.total_dice = this.data_dice.reduce((akumulasi,currentval)=>
        akumulasi + currentval.nDice,0
      )
    },
    removeDice(){
      this.data_dice.pop()
    }
  },
}
</script>

<style>
</style>
