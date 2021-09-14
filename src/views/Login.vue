<template>
  <div>
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <el-form-item label="用户名" prop="name">
        <el-input
          v-model="ruleForm.name"
          type="text"
          placeholder="请输入用户名"
        ></el-input>
      </el-form-item>

      <el-form-item label="密码" prop="password">
        <el-input
          v-model="ruleForm.password"
          type="password"
          placeholder="请输入密码"
        ></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login()"> 立即登录</el-button>
        <el-button @click="resetForm('ruleForm')">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      ruleForm: {
        name: "",
        password: "",
      },
      rules: {
        name: [
          { required: true, message: "请输入用户名", trigger: "blur" },
          { min: 2, max: 6, message: "长度在 2 到 6 个字符", trigger: "blur" },
        ],
        password: [{ required: true, message: "请输入密码", trigger: "blur" }],
      },
    };
  },
  methods: {
    login() {
      let { name, password } = this.ruleForm;
      // 这里直接跳过验证，后期完善
      //   this.$http({
      //     method: "post",
      //     url: "/get_login",
      //     data: { name: name, password: password },
      //   }).then((res) => {
      //     let { code } = res.data;
      //     if (code == "200") {
      //       sessionStorage.setItem("username", name);
      //       this.$router.push("/home");
      //     }
      //   });

      sessionStorage.setItem("username", name);
      this.$router.push("/home");
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
  },
};
</script>

<style>
</style>