<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO"
        crossorigin="anonymous">
        <link rel="stylesheet" media="screen" href="https://fontlibrary.org//face/bluu" type="text/css"/>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
body { font-size: 1em; background: #221E4E; padding: 2em; font-family: 'BluuNextBoldItalic', serif;}
.card { border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,.15); -webkit-box-shadow: 0 4px 10px rgba(0,0,0,.15); -moz-box-shadow: 0 4px 10px rgba(0,0,0,.15); background-color: #F1E6BA;}
.card-topper { border-top-right-radius: 8px; border-top-left-radius: 8px; padding: 8px 16px; font-size: 2em; font-weight: 600; text-align: center; background-color: #312823; color: #ffffff;}
.pic { max-width: 270px; max-height: 200px; padding-bottom: 1em; width: auto; height: auto;}
.titles {font-family: serif;}
#test { border: 2px solid black;}
#test td { border: 1px solid black;}
.table-responsive { overflow-x: unset; }
</style>
