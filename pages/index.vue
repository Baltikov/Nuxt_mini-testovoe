<template>
  <nuxt-link no-prefetch exact :to='"/Users"'>Все пользователи</nuxt-link>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
})
</script>

