<template>
  <div>
    <h3>Witaj {{username}}!<button @click="$emit('logout')" 
    style="color:#9b4dca;background:white;float: right;">Wyloguj</button></h3>
    
  </div>
</template>

<script>
export default {
  props: ["username"]
};
</script>

<style>
</style>