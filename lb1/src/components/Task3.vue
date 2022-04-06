<template>
  <div>
    <h1>Task 3</h1>
    <ul>
      <li
        v-for="(kasta, index) in kastas"
        v-bind:key="index"
        v-bind:class="{ has: kastas[index][0] }"
      >
        {{ index }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  mounted() {
    fetch('https://dog.ceo/api/breeds/list/all')
      .then((resp) => resp.json())
      .then((json) => {
        this.kastas = json.message;
      });
  },
  data() {
    return {
      kastas: {},
    };
  },
};
</script>

<style lang="scss" scoped>
ul {
  padding: 0;
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  li {
    width: 25%;
  }
  .has {
    color: red;
  }
}
</style>
