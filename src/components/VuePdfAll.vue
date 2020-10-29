<template>
  <div>
    <pdf v-for="i in numPages" :key="i" :src="pdfUrl" :page="i">
    </pdf>
  </div>
</template>

<script>
import pdf from 'vue-pdf'
export default {
  components: { pdf },
  data () {
    return {
      numPages: 1, // pdf文件总页数
      src: './git使用说明.pdf', // pdf文件地址
      pdfUrl: null
    }
  },

  mounted () {
    this.pdfTask(this.src)
  },
  methods: {
    pdfTask (src) {
      var self = this
      var loadingTask = pdf.createLoadingTask(src)
      loadingTask.promise.then(pdf => {
        self.pdfUrl = loadingTask
        self.numPages = pdf.numPages
      }).catch((err) => {
        console.error('pdf加载失败')
      })
    }
  }
}

</script>

<style scoped>
</style>
