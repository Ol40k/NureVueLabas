<template>
  <div id="app">
    <hr />
    <Task1 />
    <hr />
    <Task3 />
    <hr />
    <Task4 />
    <hr />
    <Task5 />
  </div>
</template>

<script>
import Task1 from '@/components/Task1.vue';
import Task3 from '@/components/Task3.vue';
import Task4 from '@/components/Task4.vue';
import Task5 from '@/components/Task5.vue';

export default {
  name: 'App',
  components: {
    Task1,
    Task3,
    Task4,
    Task5,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding-bottom: 250px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

hr {
  border: 10px double brown;
}
</style>
