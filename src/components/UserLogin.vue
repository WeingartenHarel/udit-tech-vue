<template>
  <section class="login">
    <div>Hello World User login</div>
    <input v-model="userName" placeholder="user name">
    <input v-model="userPass" placeholder="user pass">
    <button @click="sumbitUserDetails()">Login</button>
    <button @click="sumbitUserLogOut()">Logout</button>
  </section>
</template>

<script>
export default {
  props: {
    marketList: [],
  },
  data() {
    return {
      userName:null,
      userPass:null,
    };
  },
  methods: {
    sumbitUserDetails(){
      if (this.userName && this.userPass)
      this.$emit('emitUserDetail', this.userName,this.userPass);
    },
    sumbitUserLogOut(){
      this.$emit('emitUserDetail', null,null);
    }

  },
  async created() {
  },
};
</script>

<style>

</style>