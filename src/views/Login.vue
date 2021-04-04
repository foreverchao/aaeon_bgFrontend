<template>
<div class="container">
    <global-header :user="currentUser"></global-header>
    <router-view></router-view>
</div>
<div class="center">
  <h2>管理者登入</h2>
  <form class="login-form">
    <div class="mb-3">
      <label class="form-label" style="font-family:fantasy;">Email</label>
      <validate-input :rules="emailRules" v-model="emailVal"
      placeholder="請輸入電子信箱" type="text"/>
    </div>
    <div class="mb-3">
      <label class="form-label" style="font-family:fantasy;">Password</label>
      <validate-input :rules="passwordRules" v-model="passwordVal"
      placeholder="請輸入密碼" type="password"/>
    </div>
    <div class="mb-3">
      <button class="btn btn-primary" type="submit" @click.prevent="onFormSubmit">登入</button>
    </div>
  </form>
</div>
</template>

<script lang="ts">
import { defineComponent , ref } from 'vue'
import swal from 'sweetalert';
import 'bootstrap/dist/css/bootstrap.min.css'
import { useRouter } from 'vue-router' 
import GlobalHeader , { UserProps }  from '../components/GlobalHeader.vue'
import ValidateInput , { RulesProp }from '../components/ValidateInput.vue'
interface userLogin{
  emailAddr: string,
  passWord: string
}
const userInfo: userLogin = {
  emailAddr: '1111@test.com.tw' ,
  passWord: '1'
}
const currentUser: UserProps = {
    isLogin: false
}
export default defineComponent({
  components: { 
    ValidateInput,
    GlobalHeader
    },
    setup() {
      const router = useRouter() 
      
      const emailVal = ref('')
      const emailRules: RulesProp = [
        { type: 'required', message: '請輸入電子信箱' },
        { type: 'email' , message: '電子信箱不符合格式' }
      ]
      const passwordVal = ref('')
      const passwordRules: RulesProp = [
        { type: 'required', message: '請輸入密碼' }
      ]
      const onFormSubmit = () => {
        if ( userInfo.emailAddr == emailVal.value && userInfo.passWord == passwordVal.value){
          router.push('/Home')
        }else{
          swal("帳號或密碼錯誤!", "請重新輸入帳號及密碼", "error");
        }
      }
      return {
        currentUser,
        emailRules,
        passwordRules,
        onFormSubmit,
        emailVal,
        passwordVal
      }
    },
})
</script>
<style scoped>
.container {
  margin: auto;
}
.center {
  padding:30px 0px;
  margin: 0;
  text-align: center;
  margin-block-start: 0px;
}
.login-form {
  border:3px blue solid;
  margin: auto;
  position: relative;
  width: 30%;
  padding: 7px;
}
</style>