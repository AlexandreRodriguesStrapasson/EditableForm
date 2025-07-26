<template>
  <div id="a4">
    <div class="playerDataField">
      <div class="characterName">
        <input type="text" class="inputPlayerData" placeholder="Nome">
      </div>
      <div class="playerNameField">
        <input type="text" class="inputPlayerData" placeholder="Jogador">
      </div>
      <div class="classField">
        <input type="text" class="inputPlayerData" placeholder="Classe">
      </div>
      <div class="ancestryField">
        <input type="text" class="inputPlayerData" placeholder="Ancestralidade">
      </div>
      <div class="levelField">
        <input type="text" class="inputPlayerData" placeholder="LvL">
      </div>
      <div class="XpField">
        <input type="text" class="inputPlayerData" placeholder="XP">
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
  
  background-image: url('/formModel.png');
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
.ancestryField,
.classField,
.levelField,
.XpField {
  position: absolute;
  width: 28mm;
  height: 18mm;
  margin-top: -10px;
}

.characterName, .playerNameField, .classAndAncestryyField, .classField, .ancestryField, .levelField, .XpField {
  text-align: center;
  margin-top: 10px;
  padding: 0;
}

.playerNameField {
  left: 34mm;
}

.classField {
  width: 45mm;
  left: 60mm;
}

.ancestryField{
  width: 50mm;
  left: 89mm;
}

.levelField {
  left: 127mm;
}

.levelField input{
  width: 7mm;
}

.XpField{
  left: 140mm;
}

.XpField input{
  width: 16mm;
}

.inputPlayerData{
  width: 28mm;
  margin-top: 15px;
  text-align: center;
  border: none;
  font-family: 'souvenir', sans-serif;
  color: rgb(46, 46, 46);
}

.inputPlayerData:focus{
  border: solid 2px;
}
</style>