<script setup>
import { ref, onMounted, watch } from 'vue';

function toggleContrast() {
  document.body.classList.toggle('high-contrast')
}

function toggleHighlightLinks(){
  document.body.classList.toggle('highlight-links')
}
function toggleReadableFont(){
  document.body.classList.toggle('readable-font')
}
const isDarkMode = ref(false)

function toggleDarkMode() {
  isDarkMode.value = !isDarkMode.value
  if (isDarkMode.value) {
    document.body.classList.add('dark-mode')
    localStorage.setItem('darkMode', 'true')
  } else {
    document.body.classList.remove('dark-mode')
    localStorage.removeItem('darkMode')
  }
}

const isHighSpacing = ref(false)
 function toggleSpacing() {
  isHighSpacing.value = !isHighSpacing.value
  if (isHighSpacing.value) {
    document.body.classList.add('high-spacing')
    localStorage.setItem('spacingEnabled', 'true')
  } else {
    document.body.classList.remove('high-spacing')
    localStorage.removeItem('spacingEnabled')
  }
}

const isColorBlindMode = ref(false)

function toggleColorBlindMode() {
  isColorBlindMode.value = !isColorBlindMode.value
  if (isColorBlindMode.value) {
    document.body.classList.add('color-blind-mode')
    localStorage.setItem('colorBlindMode', 'true')
  } else {
    document.body.classList.remove('color-blind-mode')
    localStorage.removeItem('colorBlindMode')
  }
}
const sliderValue=ref(100)
const inputValue = ref('100')
function applyFontSize(){
  const remValue=sliderValue.value/100
  document.documentElement.style.fontSize= `${remValue}rem`
  localStorage.setItem('fontSizeValue',sliderValue.value)
}
watch(sliderValue, (newVal) => {
  inputValue.value=String(newVal)
  applyFontSize();
});
function validateAndApplyInput(){
  const parsed=parseInt(inputValue.value)
  if(!isNaN(parsed)){
    if(parsed<100) sliderValue.value=100
    else if (parsed>200) sliderValue.value=200
    else sliderValue.value=parsed
  }
}
onMounted(()=>{
  if (localStorage.getItem('spacingEnabled') === 'true') {
    isHighSpacing.value = true
    document.body.classList.add('high-spacing')
  }
  const saved = localStorage.getItem('fontSizeValue')
  if (saved){
    sliderValue.value=parseInt(saved)
    applyFontSize()
  }
  if (localStorage.getItem('colorBlindMode') === 'true') {
    isColorBlindMode.value = true
    document.body.classList.add('color-blind-mode')
  }
  if (localStorage.getItem('darkMode') === 'true') {
    isDarkMode.value = true
    document.body.classList.add('dark-mode')
  }
})
</script>

<template>
  <div class="a11y-menu-panel">
    <div class="heading">
      <h2>Accessibility Settings</h2>
    </div>
      <div id="btn1">
   <button @click="toggleContrast" :class="[
    'mode-toggle-btn',
    isDarkMode ? 'dark-active' : 'light-active-cntrst',
    isColorBlindMode ? 'cb-mode' : ''
  ]">Contrast+</button>
            
<button @click="toggleDarkMode"  :class="[
    'mode-toggle-btn',
    isDarkMode ? 'dark-active' : 'light-active-dm',
    isColorBlindMode ? 'cb-mode' : ''
  ]">
  {{ isDarkMode ? 'Light Mode' : 'Dark Mode' }}
</button>
      </div>
    <button @click="toggleColorBlindMode" :class="[isDarkMode ? 'dark-active' : 'light-active-clr',isColorBlindMode ? 'cb-mode' : '']">
  {{ isColorBlindMode ? 'Normal Colors' : 'Color Blind Mode' }}
</button>
     <button @click="toggleReadableFont"  id="font" :class="[isDarkMode ? 'dark-active' : 'light-active-dslx',
    isColorBlindMode ? 'cb-mode' : '']">Dyslexic Fonts</button>
       <span> 
          <label for="fontslider" style="font-weight: bold;">Text Size: </label>
            <input 
              id="number" 
              type="number" 
              min="100" 
              max="200" 
              v-model="inputValue" 
              style="width: 60px; margin-left: 10px;"
              @input="inputValue = $event.target.value"
              @blur="validateAndApplyInput"
              @keyup.enter="validateAndApplyInput"/>
              %
        </span>
      <input
       id="slider" 
       type="range" 
       min="100" 
       max="200" 
       step="1" 
       v-model="sliderValue" />
       
        <button @click="toggleHighlightLinks" :class="[isDarkMode ? 'dark-active' : 'light-active-link', isColorBlindMode ? 'cb-mode' : '']">
          Highlight Links
        </button>
        <button @click="toggleSpacing">
                {{ isHighSpacing ? 'Reset Spacing' : 'Increase Spacing' }}
        </button>



   </div>
</template>

<style scoped>
.a11y-menu-panel {
  position: fixed;
  bottom: 100px;
  right: 20px;
  max-height: 80vh;
  overflow-y: auto;
  width: 300px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  padding: 20px;
  z-index: 9999;
  display: flex;
  flex-direction: column;
  gap: 15px;
  ;
}

button{
  padding: 9px;
  border: none;
  border-radius: 12px;
  font-size: 1.06rem
}
.heading {
   background: linear-gradient(to right, rgba(54, 136, 250, 0.9), rgba(81, 170, 253, 0.9));
  margin-top: 0; 
  color: #333;
  font-size: 1.1em;
  text-align: center;
  margin: -20px -20px 15px -20px; 
}


.mode-toggle-btn {
  width: 50%;
  padding: 9px;
  border-radius: 12px;
  font-size: 1.06rem;
}

.light-active-dm {
  background-color: aliceblue;
  color: #000;
}
.light-active-cntrst{
  background-color: black ;
  color: #ffffff;
}
.light-active-dslx{
  background-color: antiquewhite ;
  color: #000000;
}

.light-active-link{
  background-color: rgb(250, 250, 147);
  color: #000000;
}
.light-active-clr{
  background-color: #444;
  color: #ffffff;
}
.dark-active {
  background-color: #333333;
  color: #fff;
}

.cb-mode {
  background-color: var(--cb-accent) !important;
  color: #fff !important;
}

  
#font{
  font-family: 'OpenDyslexic', Arial, sans-serif !important;
}
#btn1{
  display: flex;
  gap: 10px;
  
}

</style>



