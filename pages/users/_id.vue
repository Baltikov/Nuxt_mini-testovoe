<template>
  <div>
    <el-page-header  @back="$router.push('/Users')"
                     :content="'Карточка пользователя ' + user.name" />
    <el-user-details class="card"
                     :user="user" />
  </div>
</template>

<script>
import ElUserDetails from '../../components/ElUserDetails.vue'

export default {
  components: { ElUserDetails },
  validate ({ params }) {
    return /^\d+$/.test(params.id)
  },
  async asyncData ({ $axios, params }) {
    const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`)
    if (!user) {
      $router.push("/Error")
    }
    return { user }
  }
}
</script>

<style>
.card {
  box-shadow: 0px 2px 10px rgb(10 10 10 / 25%);
    border-radius: 6px;
    box-sizing: border-box;
    padding: 10px;
    margin-top: 15px;
}
</style>