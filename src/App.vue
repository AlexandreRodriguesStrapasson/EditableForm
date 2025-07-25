<template>
  <div id="a4">
    <div class="playerDataField">
      <div class="characterName">
        <p>Personagem:</p>
      </div>
      <div class="playerNameField">
        <p>Jogador:</p>
      </div>
      <div class="classAndAncestryyField">
        <p>Classe e Ancestralidade</p>
      </div>
      <div class="levelAndXpField">
        <p>Nível e XP</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style scoped>
#a4 {
  position: relative;
  width: 210mm;
  height: 297mm;

  border: 1px solid black;
  
  background-image: url('/formModel.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;

  margin: 20px auto;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  
  box-sizing: border-box; 
  padding: 10mm;
}
.playerDataField{
  position: absolute;
  top: 23mm;
  left: 24mm;
  width: 95mm;
  height: 21mm;
  display: flex;
  flex-direction: row;
}

.characterName,
.playerNameField,
.classAndAncestryyField,
.levelAndXpField {
  position: absolute;
  width: 28mm;
  height: 18mm;
  margin: 0;
  margin-top: -10px;
}

.characterName, .playerNameField, .classAndAncestryyField, .levelAndXpField {
  text-align: center;
}

.playerNameField {
  left: 35mm;
}

.classAndAncestryyField {
  width: 56mm;
  left: 70mm;
}

.levelAndXpField {
  width: 32mm;
  left: 135mm;
}
</style>