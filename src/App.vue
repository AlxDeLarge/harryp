<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
    <header>
        <div class="wrapper">
            <link rel="stylesheet" media="screen" href="https://fontlibrary.org/en/face/bluu" type="text/css"/>
            <div>
                <img class="tilde" src="./assets/images/tilde.png" />
            </div>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/characters">Karaktärer</RouterLink>
        <RouterLink to="/spells">Trollformler</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.wrapper {
    background-color: rgba(0, 0, 0, 0.2);
} 

.tilde {
    display: block;
    margin: auto;
}

</style>
