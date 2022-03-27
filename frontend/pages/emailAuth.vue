<template>
  <div>
    <NavBar/>
    <PasswordValidation :authData="authData"/>
  </div>
</template>

<script>
export default {
  async asyncData({error, route}){

    const {email, username, token} = route.query

    if(!email || !username || !token){

      error({status:404, message:"Not Found"})
    }

    const authData = {
      email, username, token
    }
    return {authData};
  },
}
</script>

<style>

</style>