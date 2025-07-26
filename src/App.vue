<template>
  <div>
      <div>
      <h1 >Welcome to Web Accessibility Widet</h1>
      <p>This is a demo for the accessibility widget.</p>
       <p> Web accessibility ensures that people with disabilities can participate fully in the digital world, accessing information, services, and online experiences
      </p>
      <h2>Features:</h2>
<ul>
  <li>High Contrast Mode</li>
  <li>Readable Fonts</li>
  <li>Text Spacing</li>
  <li>Dark Mode</li>
  <li>Color Blind Mode</li>
</ul>
      <div id="container">
        <img src="./assets/images.png" alt="Demo image" width="500" height="250" />
      </div>
      <p>
        <a href="https://github.com/iamharshit19">This is a demo link</a>
      </p>
    </div>

    <div class="ally-menu">
      <FloatingButton @toggle-menu="showMenu = !showMenu" />
      <MenuPanel v-if="showMenu" />
    </div>
  </div>
</template>

<script>
import FloatingButton from './components/FloatingButton.vue'
import MenuPanel from './components/MenuPanel.vue'

export default {
  components: { FloatingButton, MenuPanel },
  data() {
    return {
      showMenu: false
    }
  }
}
</script>
<style scoped>
h1{
  background-color: #333;
  color: #fff;
  margin: -20px -20px 15px -20px;
  text-align: center;
  padding-top: 25px;
  padding-bottom: 25px;
}
p{
  font-size: 1.2rem;
}
</style>
