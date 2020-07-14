
<template>
  <div class="project01">
    <section class="row">
      <div class="small-6 columns">
        <h1 class="text-center">YOU</h1>
        <div class="healthbar">
          <div
            class="healthbar text-center"
            style="background-color: green; margin: 0; color: white;"
            :style="{width:playerHealth+'%'}"
          >{{ playerHealth}}</div>
        </div>
      </div>
      <div class="small-6 columns">
        <h1 class="text-center">MONSTER</h1>
        <div class="healthbar">
          <div
            class="healthbar text-center"
            style="background-color: green; margin: 0; color: white;"
            :style="{width:monsterHealth+'%'}"
          >{{ monsterHealth}}</div>
        </div>
      </div>
    </section>
    <section class="row controls" v-if="!gameIsRunning">
      <div class="small-12 columns">
        <button id="start-game" @click="startGame">START NEW GAME</button>
      </div>
    </section>
    <section class="row controls" v-else>
      <div class="small-12 columns">
        <button id="attack" @click="attack">ATTACK</button>
        <button id="special-attack" @click="specialAttack">SPECIAL ATTACK</button>
        <button id="heal" @click="heal">HEAL</button>
        <button id="give-up" @click="giveUp">GIVE UP</button>
      </div>
    </section>
    <section class="row log">
      <div class="small-12 columns">
        <ul>
          <li></li>
        </ul>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Project01",
  data() {
    return {
      playerHealth: 100,
      monsterHealth: 80,
      gameIsRunning: false
    };
  },
  methods: {
    startGame: function() {
      this.gameIsRunning = true;
      this.playerHealth = 100;
      this.monsterHealth = 100;
    },
    attack:function(){
        var max=10;
        var min=3;
        var damage = Math.max(Math.floor(Math.random()*max)+1,min);
        this.monsterHealth -=damage;
        if(this.monsterHealth<=0){
            alert('你贏啦')
            this.gameIsRunning=false;
            return
        }
       
        
        max=7;
        min=1;
        damage = Math.max(Math.floor(Math.random()*max)+1,min);
        this.playerHealth -=damage;

        if(this.playerHealth<=0){
            alert('你輸啦');
            this.gameIsRunning=false
        }
        
    },
    specialAttack:function(){
      return 0
    },
    heal:function(){
 return 0
    },
    giveUp:function(){
 return 0
    }
  }
};
</script>

<style>
@import "../css/foundation.min.css";
@import "../css/app.css";
</style>