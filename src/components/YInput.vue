<template>
  <div>
    <input type="text" :value="value" @input="input">
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  methods: {
    input(e) {
      let inputValue = e.target.value;
      this.$emit("input", inputValue);
      this.$parent.$emit('validate');
    }
  }
};
</script>

<style lang="scss" scoped>
</style>