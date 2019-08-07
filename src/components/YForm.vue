<template>
  <div>
    <form>
      <slot></slot>
    </form>
  </div>
</template>

<script>
export default {
  provide() {
    return {
      form: this
    };
  },
  props: {
    rules: {
      type: Object
    },
    model: {
      type: Object
    }
  }
};
</script>

<style lang="scss" scoped>
</style>