<template>
  <div class="selec">
    <div
      class="opt"
      v-for="breed in breeds"
      :key="breed"
      v-on:click="
        toggle($event);
        passToParent(breed);
      "
    >
      {{ breed }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
    };
  },
  props: {
    breeds: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    passToParent(breed) {
      if (this.selected.indexOf(breed) !== -1) {
        this.selected = this.selected.filter(
          (el) => el != breed
        );
      } else {
        this.selected.push(breed);
      }

      this.$emit('click', [...this.selected]);
    },
    toggle: function (event) {
      event.target.classList.toggle('active');
    },
  },
};
</script>

<style lang="scss" scoped>
.selec {
  width: 25%;
  text-align: center;
  font-size: 18px;
  overflow: hidden;
  border: 2px solid black;
}
.opt {
  padding: 20px;
  border: 1px solid black;
}
.active {
  background-color: aqua;
}
</style>
