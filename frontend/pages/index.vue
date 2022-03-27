<template>
  <NavBar :authenticated="authenticated"/>
</template>

<script>
export default {
  async asyncData({$axios}){
    try {
      const res = await $axios.get('/admin/checkAuthStatus', {
        withCredentials: true,
      });
      return{
        authenticated: res.data.authenticated
      }
    } catch (error) {
      console.log(error);
    }
  }
}
</script>
