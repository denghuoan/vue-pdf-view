<template>
  <div>
    <iframe width="100%" height="800" scrolling="no" :src="url"></iframe>
  </div>
</template>

<script>
export default {
  computed: {
    url () {
      return `${this.baseUrl}web/viewer.html?file=${this.baseUrl}git使用说明.pdf`
    }
  },
  data () {
    return {
      baseUrl: process.env.BASE_URL
    }
  }
}
</script>

<style>
</style>
