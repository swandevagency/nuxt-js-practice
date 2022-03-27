<template>
  <NavBar yo="yooo"/>
</template>

<script>
export default {
  async asyncData({$axios}){
    try {
      const res = await $axios.get('/admin/checkAuthStatus', {
        withCredentials: true,
      });
      console.log(res.data);
    } catch (error) {
      console.log(error);
    }
  }
}
</script>
