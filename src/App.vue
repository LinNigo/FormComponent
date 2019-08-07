<template>
  <div id="app">
    <div>
      <y-form :model="ruleForm" :rules="rules" ref="ruleForm">
        <y-form-item label="用户名" prop="name">
          <y-input :value="ruleForm.name" @input="ruleForm.name=arguments[0]"></y-input>
        </y-form-item>
      </y-form>

      <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
        <el-form-item label="用户名" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input type="password" v-model="ruleForm.password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
import YInput from "./components/YInput.vue";
import YFormItem from "./components/YFormItem.vue";
import YForm from "./components/YForm.vue";
export default {
  name: "app",
  components: {
    YInput,
    YFormItem,
    YForm
  },
  data() {
    return {
      value:"",
      ruleForm: {
        name: "",
        password: ""
      },
      rules: {
        name: [
          { required: true, message: "请输入用户名" },
          { min: 3, max: 5, message: "长度在 3 到 5 个字符" }
        ],
        password: [{ required: true, message: "请输入密码" }]
      }
    };
  },
  methods: {
    submitForm(form) {
      this.$refs[form].validate(valid => {
        if (valid) {
          alert("请求登录");
        } else {
          alert("校验失败");
        }
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
