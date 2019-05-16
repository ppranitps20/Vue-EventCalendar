<template>
  <div id="app">
    <h1 class="title is-centered">Vue Calendar</h1>
    <CalendarWeek/>
    <CalendarEntry/>
  </div>
</template>

<script>
import CalendarWeek from './components/CalendarWeek.vue';
import CalendarEntry from './components/CalendarEntry.vue';

export default {
  name: 'app',
  components: {
    CalendarWeek,
    CalendarEntry,
  },
};
</script>

<style lang="scss">
html,
body {
  height: 100%;
}
</style>

<style lang="scss" scoped>
#app {
  height:auto;
  background: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
  -webkit-align-items: center;
}

.title {
  padding-bottom: 10vh;
  padding-top: 5vh;
  font-size: 4em;
  background: -webkit-linear-gradient(#2ecc71, #3498db);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
