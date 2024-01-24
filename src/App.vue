<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
    <header>
        <div class="wrapper">
            <link rel="stylesheet" media="screen" href="https://fontlibrary.org//face/bluu" type="text/css"/>
            <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->
            <div>
                <img class="tilde" src="./assets/images/tilde.png" />
            </div>
            <!--<HelloWorld msg="You did it!" />-->

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/characters">Characters</RouterLink>
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
