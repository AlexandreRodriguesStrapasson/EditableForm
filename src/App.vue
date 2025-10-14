<template>
  <div class="main-container">
    <h1>Arcana Primária</h1>

    <div class="sheet-container">
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
  
      <div id="a4_spells" v-show="showSpellSheet">
        <div class="spell_main_body">
          <div class="spell-row">
            <div class="spell-slot_1" v-for="n in 9" :key="'row1-' + n">
              <input type="text" class="spell-input">
            </div>
          </div>

          <div class="spell-row">
            <div class="spell-slot_2" v-for="n in 9" :key="'row2-' + n">
              <input type="text" class="spell-input">
            </div>
          </div>
        </div>

        <textarea class="textBox_1" placeholder="Descrição das magia"></textarea>
        <textarea class="textBox_2" placeholder="Descrição das magia"></textarea>
      </div>
    </div>

    <div class="controls">
      <button class="pdfBt" @click="exportPDF">Exportar para PDF</button>
      
      <div class="toggle-switch">
        <input type="checkbox" id="toggleSpells" v-model="showSpellSheet">
        <label for="toggleSpells">Mostrar Folha de Magias</label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import jsPDF from 'jspdf'
import html2canvas from 'html2canvas'

const showSpellSheet = ref(false)

const equipmentList = ref(Array(20).fill(''))
const firstEmptyIndex = computed(() =>
  equipmentList.value.findIndex(item => item.trim() === '')
)

const getRowStyle = (index) => {
  if (index <= 6) return { width: '70mm', marginLeft: '2mm' }
  if (index >= 7 && index <= 9) return { width: '64mm', marginLeft: '8mm' }
  if (index === 10 || index === 11) return { width: '66mm', marginLeft: '6mm' }
  if (index === 12 || index === 13) return { width: '56mm', marginLeft: '16mm' }
  if (index === 14) return { width: '69mm', marginLeft: '3mm' }
  if (index === 15) return { width: '41mm', marginLeft: '31mm' }
  if (index === 16) return { width: '36mm', marginLeft: '36mm' }
  if (index === 17) return { width: '31mm', marginLeft: '41mm' }
  if (index === 18) return { width: '28mm', marginLeft: '44mm' }
  if (index === 19) return { width: '26mm', marginLeft: '46mm' }
  return {}
}

function createTextareaOverlays(rootEl) {
  const textareas = rootEl.querySelectorAll('textarea')
  const overlays = []

  textareas.forEach((ta) => {
    const cs = getComputedStyle(ta)

    const overlay = document.createElement('div')
    overlay.className = 'textarea-print-overlay'
    overlay.textContent = ta.value

    Object.assign(overlay.style, {
      position: 'absolute',
      left: ta.offsetLeft + 'px',
      top: ta.offsetTop + 'px',
      width: ta.offsetWidth + 'px',
      height: ta.offsetHeight + 'px',
      padding: cs.padding,
      font: cs.font,
      lineHeight: cs.lineHeight,
      color: cs.color,
      background: 'transparent',
      border: 'none',
      overflow: 'hidden',
      whiteSpace: 'pre-wrap',
      wordBreak: 'break-word',
      pointerEvents: 'none',
    })

    const oldVisibility = ta.style.visibility
    ta.style.visibility = 'hidden'
    ta.parentElement.appendChild(overlay)

    overlays.push({ overlay, ta, oldVisibility })
  })

  return () => {
    overlays.forEach(({ overlay, ta, oldVisibility }) => {
      overlay.remove()
      ta.style.visibility = oldVisibility || ''
    })
  }
}

const exportPDF = async () => {
  const pdf = new jsPDF('p', 'mm', 'a4')
  const pdfWidth = pdf.internal.pageSize.getWidth()
  
  const canvasOptions = {
    scale: 1.5,
    useCORS: true,
    backgroundColor: null,
  }

  const element1 = document.getElementById('a4')
  const cleanup1 = createTextareaOverlays(element1)
  const canvas1 = await html2canvas(element1, canvasOptions)
  cleanup1()
  
  const pdfHeight1 = (canvas1.height * pdfWidth) / canvas1.width
  pdf.addImage(canvas1.toDataURL('image/png'), 'PNG', 0, 0, pdfWidth, pdfHeight1)

  if (showSpellSheet.value) {
    const element2 = document.getElementById('a4_spells')
    const canvas2 = await html2canvas(element2, canvasOptions)
    
    const pdfHeight2 = (canvas2.height * pdfWidth) / canvas2.width
    pdf.addPage()
    pdf.addImage(canvas2.toDataURL('image/png'), 'PNG', 0, 0, pdfWidth, pdfHeight2)
  }

  pdf.save('ficha.pdf')
}
</script>

<style scoped>
.main-container {
  padding: 2rem;
}

h1 {
  color: red;
  text-align: center;
  padding: 10px;
  position: relative; 
  margin-bottom: 20px; 
}

h1::after {
  content: ''; 
  position: absolute;
  bottom: 0; 
  left: 50%;
  transform: translateX(-50%);
  width: 0%;
  height: 2px;
  background-color: red;
  transition: width 1.5s ease-out;
  
  animation: expand-line 1.5s ease-out forwards;
  animation-delay: 0.5s;
}

@keyframes expand-line {
  from {
    width: 0%;
  }
  to {
    width: 100%;
  }
}

.controls {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
  position: relative;
  height: 4rem;
}

.toggle-switch {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.2rem;
}

.sheet-container {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.pdfBt {
  order: -1;
  position: absolute;
  top: 0;
  right: 2rem;
  height: 3.5rem;
  width: 15rem;
  color: red;
  background: black;
  border: red solid 1px;
  transition: 1s;
  cursor: pointer;
}

.pdfBt:hover {
  background: red;
  color: black;
}

#a4, #a4_spells {
  position: relative;
  width: 210mm;
  height: 297mm;
  border: 1px solid black;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  padding: 10mm;
  flex-shrink: 0;
}

#a4 {
  background-image: url('/img/formModel.png');
}

#a4_spells {
  background-image: url('/img/formModelSpells.png');
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

.characterName, .playerNameField, .classAndAncestryyField, .ancestryField, .classField, .levelField, .XpField {
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

.classField input {
  width: 30mm;
}

.ancestryField{
  width: 50mm;
  left: 89mm;;
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

.strengthField, .dexterityField, .constitutionField, .intelligenceField, .wisdomField, .charismaField{
  position: absolute;
  left: 23mm;
}

.strengthFieldRight, .dexterityFieldRight, .constitutionFieldRight, .intelligenceFieldRight, .wisdomFieldRight, .charismaFieldRight{
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

#strengthPoint, #dexterityPoint, #constitutionPoint, #intelligencePoint, #wisdomPoint, #charismaPoint, #strengthPointRight, #dexterityPointRight, #constitutionPointRight, #intelligencePointRight, #wisdomPointRight, #charismaPointRight{
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

#weaponNameOne, #weaponNameTwo, #weaponNameThree, #weaponNameFour, #atqWeaponOne, #atqWeaponTwo, #atqWeaponTree, #atqWeaponFour{
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

.controls {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  margin-top: 30px;
}

.toggle-switch {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1.2rem;
}

.pdfBt {
  height: 3.5rem;
  width: 15rem;
  color: red;
  background: black;
  border: red solid 1px;
  transition: 1s;
  cursor: pointer;
}

.pdfBt:hover {
  background: red;
  color: black;
}

.textBox_1, .textBox_2 {
  position: absolute;
  top: 113mm;
  height: 144mm;

  resize: none;
  border: none;
  background-color: transparent;
  outline: none;

  overflow-y: hidden; 
  
  padding: 2mm;
  font-family: inherit;
  font-size: 9px;
  box-sizing: border-box;
}

.textBox_1 {
  left: 21mm;
  width: 77mm;
}

.textBox_2 {
  left: 101mm;
  width: 75mm;
}

.spell_main_body {
  position: absolute;
  top: 73.5mm;
  left: 43mm;

  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 2mm;
}

.spell-row {
  display: flex;
  flex-direction: row;
  gap: 1.5mm;
}

.spell-slot_1 {
  width: 14mm;
  height: 8mm;
  flex-shrink: 0;
}

.spell-slot_2 {
  width: 14mm;
  height: 8mm;
  flex-shrink: 0;
}

.spell-input {
  width: 100%;
  height: 100%;
  
  border: none;
  outline: none;
  background-color: transparent;

  text-align: center;
  font-family: inherit;
  font-size: 14px;
  color: black;

  box-sizing: border-box;
}

</style>