<template>
  <div>
    <h1>Task 4</h1>
    <button v-on:click="randomize">
      PRAY TO THE GODS OF RANDOM
    </button>
    <h3>{{ randomName }}</h3>
    <ul>
      <li
        v-for="(slave, index) in subSlaves"
        v-bind:key="index"
      >
        {{ subSlaves[index] }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  methods: {
    async randomize() {
      let name = await fetch(
        'https://dog.ceo/api/breeds/list/all'
      )
        .then((resp) => resp.json())
        .then((json) => {
          this.kastas = json.message;
          this.kastaNames = Object.getOwnPropertyNames(
            json.message
          );
        })
        .then(() => {
          this.kastaNames = this.kastaNames.filter(
            (name) => this.kastas[name][0]
          );
          this.randomName =
            this.kastaNames[
              Math.floor(
                Math.random() * this.kastaNames.length
              )
            ];
          return this.randomName;
        });

      fetch(`https://dog.ceo/api/breed/${name}/list`)
        .then((resp) => resp.json())
        .then((json) => {
          this.subSlaves = json.message;
        });
    },
  },
  data() {
    return {
      kastaNames: [],
      kastas: {},
      randomName: '',
      subSlaves: {},
    };
  },
};
</script>

<style lang="scss" scoped>
button {
  padding: 20px;
  border-radius: 10px;
  border: 1px solid black;
  font-weight: 600;
  &:hover {
    background-color: blanchedalmond;
    cursor: pointer;
  }
}
ul {
  padding: 0;
  list-style: none;
}
</style>
