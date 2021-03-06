<template>
  <div>
    {{data_dice}}
    <h2>{{Number(total_dice)}}</h2>
    <button @click="addDice()">Add Dice</button>
    <button @click="roolDice()">Rool Dice</button>
    <button @click="removeDice()">Remove Dice</button>
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
        id:1,
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
