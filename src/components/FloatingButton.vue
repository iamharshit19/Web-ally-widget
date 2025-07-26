<template>
  <button class="a11y-floating-button" @click="$emit('toggle-menu')" aria-label="Accessibility Settings">
    <span class="a11y-icon" aria-hidden="true">⚙️</span>
    <span class="a11y-sr-only">Accessibility Settings</span>
  </button>
</template>

<style scoped>
.a11y-floating-button {
  position: fixed;
  bottom: 25px;
  right: 20px;
  background-color: #007bff; 
  color: white;
  border: none;
  border-radius: 50%; 
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: background-color 0.3s ease, transform 0.3s ease;
  z-index: 10000; 
}


.a11y-floating-button:hover {
  background-color: #0056b3; 
  transform: translateY(-2px); 
}

.a11y-floating-button:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.a11y-icon {
  line-height: 1; 
}


.a11y-sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
</style>
