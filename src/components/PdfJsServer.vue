<template>
  <div class="pdf_page">
    <iframe width="100%" height="800" scrolling="no" :src="url"></iframe>
  </div>
</template>

<script>
export default {
  computed: {
    url () {
      return `${this.serverUrl}web/viewer.html?file=${encodeURIComponent(this.serverUrl + 'git使用说明.pdf')}`
    }
  },
  data () {
    return {
      serverUrl: 'http://192.168.0.26:9999/pdfView/'
    }
  }
}
</script>

<style>
</style>
