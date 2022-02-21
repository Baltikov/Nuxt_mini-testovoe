<template>
  <el-container>
    <el-header>
      <h1>
        <span v-if="$route.params.id">{{ $route.query.name }}</span>
        <span v-else>Все пользователи</span>
      </h1>
    </el-header>
    <el-main><Nuxt/></el-main>
  </el-container>
</template>

<script>
export default {

}
</script>