<template>
   <div>
    <h1>Ошибка {{ error.statusCode }}</h1>
     <el-page-header  @back="$router.push('/Users')"/>
   </div>
</template>

<script>
export default {
  props: {
    error: {
      type: Object,
      required: true
    }
  }
}
</script>
