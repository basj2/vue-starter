<template>
  <div>
    <h3>Witaj {{username}}!</h3>
    <a @click="$emit('logout')">Wyloguj</a>
  </div>
</template>

<script>
export default {
  props: ["username"]
};
</script>

<style>
</style>