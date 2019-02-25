<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <form>
      <input type="text" name="username" v-model="username"> <br>
      <input type="text" name="password" v-model="password"> <br>
      <a href="javascript:;" @click="addUser">提交</a>
    </form>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      username: '',
      password: ''
    }
  },
  methods: {
    addUser() {
      var username = this.username;
      var password = this.password;

      if(!username){
        console.log('账号不能为空!')
      }else{
        if(!password){
          console.log('密码不能为空!')
        }else{
          this.$axios.post('http://login.api.test.daipianpian.com/api/user/addUser', {
            username: username,
            password: password
          },{}).then((response) => {
            console.log(response);
          })          
        }       
      }
    }
  }
}
</script>