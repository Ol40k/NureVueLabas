<template>
  <div class="selec-div" ref="selec">
    <h3 v-if="this.tit">{{ this.tit }}</h3>
    <h3 v-else>Default title rendered 😢</h3>
    <select
      v-model="selected"
      multiple="true"
      :size="this.breeds.length / 10"
      v-on:change="passToParent"
      v-bind:class="{ 'sel-default': defaultClass }"
    >
      <option
        v-for="breed in breeds"
        :key="breed"
        :value="breed"
      >
        {{ breed }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      defaultClass: true,
    };
  },
  props: {
    breeds: {
      type: Array,
      default() {
        return [];
      },
    },
    tit: { type: String },
  },
  methods: {
    passToParent() {
      this.$emit('changed', [...this.selected]);
    },
  },
  mounted() {
    if (this.$refs.selec.classList.length > 1) {
      this.defaultClass = false;
    }
  },
};
</script>

<style lang="scss" scoped>
.selec-div {
  width: 25%;
  display: flex;
  flex-direction: column;
}

select {
  width: 100%;
  height: 100%;
  text-align: center;
  font-size: 18px;
  overflow: hidden;
}

.sel-light {
  option {
    background-color: lightblue;
  }
}

.sel-dark {
  option {
    background-color: darkkhaki;
  }
}

.sel-default {
  option {
    background-color: #dcd8e3;
  }
}
</style>
