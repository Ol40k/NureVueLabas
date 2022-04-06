<template>
  <div class="task1">
      <h1>Task 1 And 2</h1>
    <input type="text" v-model="message" />
    <p>Привет {{ pogonyalo(message) }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
    };
  },
  methods: {
    pogonyalo(mes) {
      if (mes === '') {
        return 'незнакомец';
      }
      return mes;
    },
  },
};
</script>

<style scoped lang="scss">
input {
  padding: 10px;
  border-radius: 10px;
  font-weight: 600;
}
</style>
