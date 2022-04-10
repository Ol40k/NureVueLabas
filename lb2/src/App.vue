<template>
  <div id="app">
    <h1>Use ctrl to select multiple</h1>
    <div class="lists">
      {{/*task 4: try to pass class (sel-light, sel-dark) or header*/ }}
      <List class="sel-light" tit="Sample 😀" :breeds="breeds" @changed="childChanged" />
      <List class="sel-dark" :breeds="selectedBreeds" />
    </div>
    <hr>
    <h1>TASK 5</h1>
    <div class="lists">   
      <DivList  :breeds="breeds" @click="childClicked" />
      <DivList  :breeds="selectedBreedsDiv" />
    </div>
  </div>
</template>

<script>
import List from '@/components/List.vue';
import DivList from '@/components/DivList.vue';

export default {
  name: 'App',
  components: {
    List,
    DivList,
  },
  data() {
    return {
      breeds: [],
      selectedBreeds: [],
      selectedBreedsDiv: [],
    };
  },
  mounted() {
    fetch('https://dog.ceo/api/breeds/list/all')
      .then((resp) => resp.json())
      .then((json) => {
        this.breeds = Object.getOwnPropertyNames(
          json.message
        );
      });
  },
  methods: {
    childChanged(list) {
      this.selectedBreeds = [...list];
    },
    childClicked(list) {
      this.selectedBreedsDiv = [...list];
    }
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.lists {
  display: flex;
  justify-content: space-evenly;
}
</style>
