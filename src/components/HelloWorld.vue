<script>
export default {
  data() {
    return {
      scoreone: 0,
      scoretwo: 0,
      playing: false,
      playerChoice: "",
      computerChoice: "",
      result: "",
      gameOver: false,
      heartchoice: "src/img/heart.png"
    };
  },
  methods: {
    playGame() {
      const choices = ["src/img/rock.png", "src/img/paper.png", "src/img/cut.png", "src/img/heart.png"];
      this.playerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.computerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.calculateResult();
      this.playing = true;
    },
    calculateResult() {
      if (this.playerChoice === this.computerChoice) {
        this.result = "DRAW";
      } else if (this.playerChoice === "src/img/heart.png") {
        this.result = "playerOne WIN";
        this.scoreone += 1;
      } else if (this.computerChoice === "src/img/heart.png") {
        this.result = "playerTwo WIN";
        this.scoretwo += 1;
      } else if (
        (this.playerChoice === "src/img/rock.png" && this.computerChoice === "src/img/cut.png") ||
        (this.playerChoice === "src/img/paper.png" && this.computerChoice === "src/img/rock.png") ||
        (this.playerChoice === "src/img/cut.png" && this.computerChoice === "src/img/paper.png")
      ) {
        this.result = "playerOne WIN";
        this.scoreone += 1;
        this.scoretwo += 0;
      } else {
        this.result = "playerTwo WIN";
        this.scoreone += 0;
        this.scoretwo += 1;
      }
    },
    resetGame() {
      this.playing = false;
      this.playerChoice = "";
      this.computerChoice = "";
      this.result = "";
      this.gameOver = false;
      // ตั้งค่า scoreone และ scoretwo เป็น 0 เมื่อรีเซ็ตเกม
      this.scoreone = 0;
      this.scoretwo = 0;
    },
  },
};
</script>
<template>
  <div class="col-center">
    <div>
      <h1 >Rock Paper Scissors</h1>
      <div class="row-center">
        <!-- <div class="iconsize">
          <i v-if="!playing" class="fa-regular fa-hand-scissors"></i>
          <i v-if="!playing" class="fa-regular fa-hand-back-fist"></i>
          <i v-if="!playing" class="fa-regular fa-hand"></i>
        </div> -->
        <img v-if="!playing" src="src/img/rockpaper.png" alt="Rock Paper" class="img_cover" /><br>
        <div class="row">
          <div class="col -center">
            <button @click="playGame" :disabled="gameOver"  class="fa-solid fa-play" style="border-color: #245936;" ></button>
          </div>
          
          </div>

      </div>
  </div>
  
  </div>
  <div>
    
    <div v-if="playing" class="row">
  <div class="col-sm-6 mb-3 mb-sm-0">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title" style="font-size: 30px;">playerOne </h5>
        
          <h2><img :src="playerChoice" class="img_game"  alt="player one Choice"></h2>
          
          
          <p>scoreplayerOne: {{ scoreone }}</p>
      </div>
    </div>
  </div>
  <div class="col-sm-6 mb-3 mb-sm-0">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title" style="font-size: 30px;" >playerTwo  </h5>
        
          
          <h2><img :src="computerChoice" class="img_game" alt="player two Choice"> </h2>
          
          
          <p>scoreplayerTwo: {{ scoretwo }}</p>
        
      </div>
    </div>
  </div>
  <div class="col-center">
    <div class="card">
      <h3> {{ result }}</h3>
      <div class="col-center">
            <button v-if="playing" @click="resetGame" class="fa-solid fa-rotate-right" style="border-color: #245936;"></button> 
       </div>
  </div>
  </div>
</div>
  </div>
  
  
</template>




<style scoped>
.read-the-docs {
  color: #888;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.card {
  padding: 20px;
  margin: 10px;
  border-color: #5FA777;
  background-color: #EFF6F1 ;
}
.iconsize{
  height: 2em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
  
}
</style>
