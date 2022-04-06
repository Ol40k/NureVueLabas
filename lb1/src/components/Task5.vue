<template>
  <div>
    <div class="buttons">
      <button v-on:click="add">ADD</button>
      <button v-on:click="remove">REMOVE</button>
      <button v-on:click="randomize">GO CRAZY</button>
    </div>
    <ul>
      <li v-for="kasta in toShowList" v-bind:key="kasta">
        {{ kasta }}
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
        this.kastas = Object.getOwnPropertyNames(
          json.message
        );
      });
  },
  data() {
    return {
      kastas: [],
      toShowList: [],
    };
  },
  methods: {
    add() {
      if (this.kastas.length === 0) return;
      const ranName =
        this.kastas[
          Math.floor(Math.random() * this.kastas.length)
        ];
      this.toShowList.push(ranName);
      this.kastas = this.kastas.filter(
        (el) => el !== ranName
      );
    },
    remove() {
      if (this.toShowList.length === 0) return;
      const ranName =
        this.toShowList[
          Math.floor(Math.random() * this.toShowList.length)
        ];
      this.kastas.push(ranName);
      this.toShowList = this.toShowList.filter(
        (el) => el !== ranName
      );
    },
    randomize() {
      if (this.toShowList.length === 0) return;
      const refArray = [...this.toShowList];
      let currentIndex = refArray.length,
        randomIndex;
      while (currentIndex != 0) {
        randomIndex = Math.floor(
          Math.random() * currentIndex
        );
        currentIndex--;

        [refArray[currentIndex], refArray[randomIndex]] = [
          refArray[randomIndex],
          refArray[currentIndex],
        ];
      }
      this.toShowList = [...refArray];
    },
  },
};
</script>

<style lang="scss" scoped>
ul {
  list-style: none;
  padding: 0;
}
.buttons {
  display: flex;
  justify-content: space-evenly;
}
button {
  min-width: 25%;
  padding: 20px;
  border-radius: 10px;
  border: 1px solid black;
  font-weight: 600;
  &:hover {
    background-color: blanchedalmond;
    cursor: pointer;
  }
}
</style>
