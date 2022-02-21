<template>
  <div >
    <div v-for="(item, key) in user"
      :key="key"
      >
      <ul
        v-if="typeof item === 'object'"
      >
        <span class="bold">{{ key + ": " }}</span>
        <el-user-details
          :user="item"
          class="mr-l"
        />
      </ul>
        <ul v-else>
          <span class="bold">{{ key + ": " }}</span>
          <span>{{ item }}</span>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ElUserDetails',
  props: {
    user: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style scoped>
.mr-l {
    margin-left: 30px;
}
.bold {
  font-weight: bold;
}

</style>