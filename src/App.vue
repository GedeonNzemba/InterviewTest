<template>
  <div id="app">
    <label>
      <input type="number" v-model="limit" />
    </label>
    <Numbers :limit="limit"/>
  </div>
</template>

<script>
import Numbers from '@/components/Numbers';

export default {
  name: 'App',
  components: {Numbers},
  data() {
    return {
      limit: 100
    }
  }
}
</script>

<style scoped>
</style>
