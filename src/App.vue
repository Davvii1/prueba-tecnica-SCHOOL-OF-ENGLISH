<script setup>
import ListaContactosOp from './components/ListaContactosOp.vue'
import Chat from './components/Chat.vue'
</script>

<template>
  <!-- <HelloWorld msg="You did it!" /> -->
  <div class="app-container">
    <ListaContactosOp />
    <Chat />
  </div>
</template>

<style scoped>
.app-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: row;
  align-items: center;
}
</style>
