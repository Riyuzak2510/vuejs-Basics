<template>
  <div id="app" class="container">
    <h1 class="text-center">Player Score Counter</h1>
    <div class="card">
      <div class="card-body text-center">
        <h3>Player 1</h3>
        <button @click="incscore1()" type="button" class="btn btn-success">Up</button>
        <span class = "player-score1"> {{player_1_score}} </span>
        <button @click="decscore1()" type="button" class="btn btn-danger">Down</button>
      </div>
      <div class="card-body text-center">
        <h3>Player 2</h3>
        <button @click="incscore2()" type="button" class="btn btn-success">Up</button>
        <span class = "player-score2"> {{player_2_score}} </span>
        <button @click="decscore2()" type="button" class="btn btn-danger">Down</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      player_1_score:0,
      player_2_score:0
    }
  },
  methods : {
    incscore1(){
      this.player_1_score++;
    },
    decscore1(){
      if(this.player_1_score > 0)
      {
        this.player_1_score--;
      }
    },
    incscore2(){
      this.player_2_score++;
    },
    decscore2(){
      if(this.player_2_score > 0)
      {
        this.player_2_score--;
      }
    }
  }
}
</script>

<style>
.player-score1{
  font-size: 2em
}
.player-score2{
  font-size: 2em
}
</style>