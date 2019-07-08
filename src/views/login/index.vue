<template>
  <div class='login'>
    <van-nav-bar title="登陆" />
    <form>
      <van-cell-group>
        <van-field
          v-model="user.mobile"
          required
          clearable
          label="手机号"
          placeholder="请输入手机号"
        />
        <van-field
          v-model="user.code"
          type="password"
          label="验证码"
          placeholder="请输入验证码"
          required
        />
      </van-cell-group>
      <div class='loginBtn'>
        <van-button
          type="info"
          class='btn'
          @click.prevent='handleLogin'
        >登陆</van-button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Login',
  data () {
    return {
      user: {
        mobile: '15603266036',
        code: '123456'
      }
    }
  },
  methods: {
    async handleLogin () {
      const res = await axios({
        method: 'POST',
        url: 'http://toutiao.course.itcast.cn/app/v1_0/authorizations',
        data: this.user
      })
      console.log(res)
    }
  }
}
</script>
<style lang='less' scoped>
.loginBtn {
  padding: 10px;
  .btn {
    width: 100%;
  }
}
</style>
