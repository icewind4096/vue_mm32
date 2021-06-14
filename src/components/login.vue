<template>
  <div class="loginContainer">
    <div class="loginBox">
      <!-- 头像区域-->
      <div class="avatarBox">
        <img class="avatarLogin" src="../assets/logo.png" />
      </div>

      <!-- 表单区域-->
      <el-form ref="loginFormRef" class="loginForm" label-width="0px" :model="loginFormData" >
        <!--用户名-->
        <el-form-item prop="userName">
          <el-input v-model="loginFormData.userName" placeholder="请输入用户名" prefix-icon="iconfont icon-xingmingyonghumingnicheng"></el-input>
        </el-form-item>
        <!--密码-->
        <el-form-item prop="password">
          <el-input v-model="loginFormData.password" placeholder="请输入密码" prefix-icon="iconfont icon-mima"></el-input>
        </el-form-item>
        <el-form-item class="buttons">
          <el-button type="primary" @click="login">登录</el-button>
          <el-button type="info" @click="resetLoginForm">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginFormData: {
        userName: '',
        password: ''
      },
      token: 'mm32loginsuccess'
    }
  },
  methods: {
    async login () {
      this.$message.success('登录成功')
      window.sessionStorage.setItem('token', this.token)
      // 把页面路由到/home
      await this.$router.push('/home')
    },
    resetLoginForm () {
      this.$refs.loginFormRef.resetFields()
    }
  }
}
</script>

<style lang="less" scoped>

.loginContainer{
  background-color: #2b4b6b;
  height: 100%;
}

.loginBox{
  position: absolute;
  width: 450px;
  height: 300px;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  border-radius: 3px;
  .avatarBox{
    position: absolute;
    left: 50%;
    height: 130px;
    width: 130px;
    border: #eee solid 1px;
    padding: 10px;
    border-radius: 50%;
    box-shadow: 0 0 10px #ddd;
    transform: translate(-50%, -50%);
    background-color: #fff;
      .avatarLogin{
        height: 100%;
        width: 100%;
        border-radius: 50%;
        background-color: #eee;
      }
  }
}

.loginForm{
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
  .buttons{
    display: flex;
    justify-content: flex-end;
  }
}

</style>
