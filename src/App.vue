<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ul>
      <li class="user_debug" v-for="user in userList" :key="user._id" >
          {{user}}
        </li>
      </ul>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <UserLogin v-on:emitUserDetail="setUserDetials" />
    <HomePage  v-if="user"/>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import HomePage from './components/HomePage.vue'
import UserLogin from './components/UserLogin.vue'

// 

export default {
  name: 'App',
  data() {
    return {
     user:'null',
     userList:[
       {
         userName:'admin001',
         userPass:'1234'
       },
       {
         userName:'admin002',
         userPass:'1234'
       }
     ]
    };
  },
  methods:{
    setUserDetials(userName,userPass){
      console.log(userName,userPass)
      this.userList.map((user) =>{
          if (userName === null && userPass===null) this.user = null;
          if (user.userName === userName && user.userPass === userPass){
              this.user = user
          }
      })
    }
  },
  components: {
    HelloWorld,
    HomePage,
    UserLogin,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
