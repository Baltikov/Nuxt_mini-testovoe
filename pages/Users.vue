<template>
  <div>
    <el-table :items="users" />
  </div>
</template>

<script>
import ElTable from "@/components/ElTable.vue";

export default {
    components: {ElTable},
    async asyncData ({ $axios }) {
        const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
        return {users}
    },
}
</script>

<style>

</style>