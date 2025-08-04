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
      <input type="text" id="pvField" placeholder="00">
      <input type="text" id="caField" placeholder="00">
      <input type="text" id="levelBonusField" placeholder="00">
      <input type="text" id="movField" placeholder="00">
    </div>

    <div class="vrmField">
      <input type="text" id="vigorField"    placeholder="00">
      <input type="text" id="reflexesField" placeholder="00">
      <input type="text" id="magicField"    placeholder="00">
    </div>

    <div class="weaponsFields">
      <input type="text" id="weaponNameOne"   placeholder="Espada curta">
      <input type="text" id="weaponNameTwo"   placeholder="2x Lança">
      <input type="text" id="weaponNameThree" placeholder="Adaga">
      <input type="text" id="weaponNameFour"  placeholder="Arco curto">

      <input type="text" id="atqWeaponOne"  placeholder="10">
      <input type="text" id="atqWeaponTwo"  placeholder="10">
      <input type="text" id="atqWeaponTree" placeholder="10">
      <input type="text" id="atqWeaponFour" placeholder="10">

      <input type="text" id="dmgWeaponOne"  placeholder="10">
      <input type="text" id="dmgWeaponTwo"  placeholder="10">
      <input type="text" id="dmgWeaponTree" placeholder="10">
      <input type="text" id="dmgWeaponFour" placeholder="10">

      <input type="text" id="mvnWeaponOne"  placeholder="10">
      <input type="text" id="mvnWeaponTwo"  placeholder="10">
      <input type="text" id="mvnWeaponTree" placeholder="10">
      <input type="text" id="mvnWeaponFour" placeholder="10">
    </div>

    <div class="moneyFields">
      <input type="text" id="poField" placeholder="100"><br>
      <input type="text" id="ppField" placeholder="100"><br>
      <input type="text" id="pcField" placeholder="100">
    </div>

    <div class="equipmentsField">
      <input
        v-for="(item, index) in equipmentList"
        :key="index"
        v-model="equipmentList[index]"
        :placeholder="index === firstEmptyIndex ? '...' : ''"
        :style="getRowStyle(index)"
      >
    </div>

    <div class="skillsField">
      <div>
        <textarea class="skillFieldOne" placeholder="Bola de fogo"></textarea>
        <textarea class="skillFieldTwo" placeholder="..."></textarea>
        <textarea class="skillFieldThree" placeholder="..."></textarea>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const equipmentList = ref(Array(20).fill(''))

const firstEmptyIndex = computed(() =>
  equipmentList.value.findIndex(item => item.trim() === '')
)

const getRowStyle = (index) => {
  if (index <= 6) {
    return { width: '70mm', marginLeft: '2mm' };
  }
  if (index >= 7 && index <= 9) {
    return { width: '64mm', marginLeft: '8mm' };
  }
  if (index === 10 || index === 11) {
    return { width: '66mm', marginLeft: '6mm' };
  }
  if (index === 12 || index === 13) {
    return { width: '56mm', marginLeft: '16mm' };
  }
  if (index === 14) {
    return { width: '69mm', marginLeft: '3mm' };
  }
  if (index === 15) {
    return { width: '41mm', marginLeft: '31mm' };
  }
  if (index === 16) {
    return { width: '36mm', marginLeft: '36mm' };
  }
  if (index === 17) {
    return { width: '31mm', marginLeft: '41mm' };
  }
  if (index === 18) {
    return { width: '28mm', marginLeft: '44mm' };
  }
  if (index === 19) {
    return { width: '26mm', marginLeft: '46mm' };
  }
  return {};
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
  left: 28mm;
}

#movField{
  top: 42mm;
  right: 2mm;
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

#weaponNameOne, #weaponNameTwo, #weaponNameThree, #weaponNameFour,
#atqWeaponOne, #atqWeaponTwo, #atqWeaponTree, #atqWeaponFour{
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

#atqWeaponOne, #atqWeaponTwo, #atqWeaponTree, #atqWeaponFour{
  position: relative;
  width: 16mm;
}

#atqWeaponOne{
    top: 5mm;
    left: 13mm;
}

#atqWeaponTwo{
  top: 13mm;
  right: 4mm;
}

#atqWeaponTree{
  top: 20.5mm;
  right: 21mm;
}

#atqWeaponFour{
  top: 28mm;
  right: 38mm;
}

#dmgWeaponOne, #dmgWeaponTwo, #dmgWeaponTree, #dmgWeaponFour{
  position: relative;
  text-align: center;
  border: none;
  width: 12mm;
}

#dmgWeaponOne{
  bottom: 1mm;
  left: 64mm;
}

#dmgWeaponTwo{
  top: 7.5mm;
  left: 51mm;
}

#dmgWeaponTree{
  top: 15mm;
  left: 38mm;
}

#dmgWeaponFour{
  top: 23mm;
  left: 25mm;
}

#mvnWeaponOne, #mvnWeaponTwo, #mvnWeaponTree, #mvnWeaponFour{
  position: relative;
  text-align: center;
  border: none;
  width: 18mm;
}

#mvnWeaponOne{
  bottom: 0.7mm;
  left: 31mm;
}

#mvnWeaponTwo{
  top: 7.5mm;
  left: 12mm;
}

#mvnWeaponTree{
  top: 9.5mm;
  left: 83.5mm;
}

#mvnWeaponFour{
  top: 17mm;
  left: 64mm;
}

.moneyFields{
  position: absolute;
  width: 28mm;
  height: 21mm;
  bottom: 5mm;
  left: 62mm;
}

.moneyFields input{
  border: none;
  position: relative;
  text-align: center;
  left: 6.5mm;
  width: 12mm;
}

.equipmentsField{
  position: absolute;
  width: 76mm;
  height: 115mm;
  top: 156mm;
  left: 15mm;
}

.equipmentsField input{
  border: none;
  background-color: transparent;
}

.skillsField{
  position: absolute;
  width: 97mm;
  height: 63mm;
  left: 92mm;
  top: 156mm;
}

.skillsField .skillFieldOne {
  width: 100%;
  height: 62mm;
  
  overflow-y: hidden; 
  border: none;
  resize: none;
  box-sizing: border-box;
  background-color: transparent;
  padding: 2mm;
  
  font-family: inherit;
  font-size: 14px;
}

.skillsField .skillFieldTwo {
  width: 86mm;
  height: 43mm;
  
  margin-top: -3.5mm;
  overflow-y: hidden; 
  border: none;
  resize: none;
  box-sizing: border-box;
  background-color: transparent;
  padding: 2mm;
  
  font-family: inherit;
  font-size: 14px;
}

.skillsField .skillFieldThree {
  width: 77mm;
  height: 38mm;

  margin-top: -5.5mm;
  overflow-y: hidden; 
  border: none;
  resize: none;
  box-sizing: border-box;
  background-color: transparent;
  padding: 2mm;
  
  font-family: inherit;
  font-size: 14px;
}

.skillsField textarea:focus {
  outline: none;
}
</style>