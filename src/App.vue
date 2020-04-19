<template>
  <div id="app">
    <calendar-constructor />
  </div>
</template>

<script>
import CalendarConstructor from "@/components/CalendarConstructor";
export default {
  name: "App",
  components: {
    CalendarConstructor
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
