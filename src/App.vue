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

    <div class="attributePointsField">
        <div class="strengthField">
          <input type="text" id="strengthPoint" placeholder="20">
        </div>

        <div class="strengthFieldRight">
          <input type="text" id="strengthPointRight" placeholder="20">
        </div>

        <div class="dexterityField">
          <input type="text" id="dexterityPoint" placeholder="20">
        </div>

        <div class="dexterityFieldRight">
          <input type="text" id="dexterityPointRight" placeholder="20">
        </div>

        <div class="constitutionField">
          <input type="text" id="constitutionPoint" placeholder="20">
        </div>

        <div class="constitutionFieldRight">
          <input type="text" id="constitutionPointRight" placeholder="20">
        </div>

        <div class="intelligenceField">
          <input type="text" id="intelligencePoint" placeholder="20">
        </div>

        <div class="intelligenceFieldRight">
          <input type="text" id="intelligencePointRight" placeholder="20">
        </div>

        <div class="wisdomField">
          <input type="text" id="wisdomPoint" placeholder="20">
        </div>

        <div class="wisdomFieldRight">
          <input type="text" id="wisdomPointRight" placeholder="20">
        </div>

        <div class="charismaField">
          <input type="text" id="charismaPoint" placeholder="20">
        </div>

        <div class="charismaFieldRight">
          <input type="text" id="charismaPointRight" placeholder="20">
        </div>
    </div>

    <div class="statusField">
        <input type="text" id="pvField"         placeholder="00">
        <input type="text" id="caField"         placeholder="00">
        <input type="text" id="levelBonusField" placeholder="00">
        <input type="text" id="movField"        placeholder="00">
    </div>

    <div class="vrmField">
      <input type="text" id="vigorField"    placeholder="00">
      <input type="text" id="reflexesField" placeholder="00">
      <input type="text" id="magicField"    placeholder="00">
    </div>

    <div class="weaponsFields">
        <input type="text" id="weaponNameOne" placeholder="Espada curta">
        <input type="text" id="weaponNameTwo" placeholder="2x Lança">
        <input type="text" id="weaponNameThree" placeholder="Adaga">
        <input type="text" id="weaponNameFour" placeholder="Arco curto">
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
  
  background-image: url('/img/formModel.png');
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
  left: 84mm;;
}

.ancestryField input{
  width: 30mm;
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
  width: 20mm;
  margin-top: 15px;
  text-align: center;
  border: none;
  color: rgb(46, 46, 46);
}

.inputPlayerData:focus{
  border: solid 2px;
}

.attributePointsField{
  position: relative;
  width: 76mm;
  height: 99mm;
  top: 33mm;
  left: 4mm;
}

.strengthField, .dexterityField, .constitutionField, .intelligenceField, .wisdomField,
.charismaField{
  position: absolute;
  left: 23mm;
}

.strengthFieldRight, .dexterityFieldRight, .constitutionFieldRight, .intelligenceFieldRight, 
.wisdomFieldRight, .charismaFieldRight{
  position: absolute;
  left: 36mm;
}

.strengthField{
  top: 2mm;
}

.strengthFieldRight{
  top: 8mm;
}

.dexterityField{
  top: 18mm;
}

.dexterityFieldRight{
  top: 25mm;
}

.constitutionFieldRight{
  top: 42mm;;
}

.intelligenceFieldRight{
  top: 57mm;
}

.wisdomFieldRight{
  top: 73mm;
}

.charismaFieldRight{
  top: 91mm;
}

.constitutionField{
  top: 35mm;
}

.intelligenceField{
  top: 51mm;
}

.wisdomField{
  top: 67mm;
}

.charismaField{
  top: 82mm;
}

#strengthPoint, #dexterityPoint, #constitutionPoint, #intelligencePoint, #wisdomPoint,
#charismaPoint, #strengthPointRight, #dexterityPointRight, #constitutionPointRight, #intelligencePointRight,
#wisdomPointRight, #charismaPointRight{
  width: 30px;
  height: 20px;
  text-align: center;
  border: none;
  color: rgb(46, 46, 46);
}

.statusField{
    position: absolute;
    left: 91mm;
    top: 42mm;
    width: 73mm;
    height: 60mm;
}

.statusField input{
  border: none;
}

#pvField, #caField, #levelBonusField, #movField{
  position: relative;
  text-align: center;
  width: 10mm;
  height: 10mm;
}

#pvField{
  top: 7mm;
  left: 30mm;
}

#caField{
  top: 23mm;
}

#levelBonusField{
  top: 23mm;
  left: 25mm;
}

#movField{
  top: 40mm;
  right: 5mm;
}

.vrmField{
  position: absolute;
  width: 32mm;
  height: 64mm;
  left: 166mm;
  top: 39mm;
}

#vigorField, #reflexesField, #magicField{
  position: relative;
  text-align: center;
  left: 2mm;
  height: 8mm;
  width: 24mm;
  border: none;
}

#vigorField{
  top: 11mm;
}

#reflexesField{
  top: 24mm;
}

#magicField{
  top: 36mm;
}

.weaponsFields{
  position: absolute;
  width: 106mm;
  height: 42mm;
  left: 90mm;
  top: 103mm;
}

#weaponNameOne, #weaponNameTwo, #weaponNameThree, #weaponNameFour {
  position: relative;
  width: 30mm;
  height: 5mm;
  border: none;
  text-align: center;
}

#weaponNameOne{
  top: 11mm;
  left: 6mm;
}

#weaponNameTwo{
  top: 18.7mm;
  right: 25mm;
}

#weaponNameThree{
  top: 26.3mm;
  right: 56mm;
}


#weaponNameFour{
  top: 28.4mm;
  left: 6mm;
}
</style>