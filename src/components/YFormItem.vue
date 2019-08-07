<template>
  <div>
    <label :prop="prop">{{label}}</label>
    <slot></slot>
    <p>{{error}}</p>
  </div>
</template>

<script>
//需要知道何时去校验
import Schema from "async-validator";
export default {
  inject: ["form"],
  props: {
    prop: {
      type: String,
      default: ""
    },
    label: {
      type: String,
      default: ""
    }
  },
  data() {
      return {
          error: ''
      }
  },
  methods: {
    validate() {
      const rules = this.form.rules[this.prop]; //数组
      const value = this.form.model[this.prop];
      const descriptor = { [this.prop]: rules };
      const schema = new Schema(descriptor);
      schema.validate({ [this.prop]: value }, errors => {
        if (errors) {
          this.error = errors[0].message;
        } else {
          this.error = "";
        }
      });
    }
  },
  mounted() {
    this.$on("validate", this.validate);
  }
};
</script>

<style lang="scss" scoped>
</style>