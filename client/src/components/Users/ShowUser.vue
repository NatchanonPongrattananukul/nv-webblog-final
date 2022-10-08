<template>
  <div>
    <h1>Show User</h1>
    <p>id: {{ userId }}</p>
    <p>ชื่อ - นามสกุล {{ user.name }} - {{ user.lastname }}</p>
    <p>email: {{ user.email }}</p>
    <p>password: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
  return {
    users: []
  }
},
    async created() {

  this.user = (await UsersService.index()).data
  this.users = (await UsersService.index()).data
  let result = (await UsersService.index()).data
  console.log(result)
  console.log(this.user)

},
/*  async created()
{
    this.users = (await UsersService.index()).data
    this.user = (await UsersService.index()).data
},*/
methods: {
  navigateTo(route) { this.$router.push(route) },
        async deleteUser(user) {
    try {
      await UsersService.delete(user)
      this.refreshData()
    } catch (err) {
      console.log(err)
    }
  },
        async refreshData() {
    this.users = (await UsersService.index()).data
  }
}

};
  /*data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};*/



</script>
<style scoped>
</style>