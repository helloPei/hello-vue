<template>
  <div>
    <el-form ref="form" :model="form" :rules="rules" label-width="80px;" class="login-box">
      <h1 class="login-title">登录</h1>
      <el-form-item label="账号" prop="username">
        <el-input type="text" placeholder="请输入账号" v-model="form.username"/>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input type="password" placeholder="请输入密码" v-model="form.password"/>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit('form')">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  export default {
    name: "Login",
    data() {
      return {
        form: {
          username: '',
          password: ''
        },
        rules: {
          username: [
            { required: true, message: '请输入账号', trigger: 'blur' }
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      onSubmit(form) {
        this.$refs[form].validate((valid) => {
          if (valid) {
            //编程式导航,传参数
            this.$router.push({name: 'Main', params: {username: this.form.username}});
          } else {
            this.$message({
              message: '请输入账号和密码',
              type: 'warning'
            });
            return false;
          }
        });
      }
    }
  }
</script>

<style lang="scss" scoped>
  .login-box {
    width: 350px;
    margin: 150px auto;
    border: 1px solid #DCDFE6;
    padding: 20px;
    border-radius: 20px;
    box-shadow: 0 0 25px #DCDFE6;
  }
  .login-title {
    text-align: center;
  }
</style>
