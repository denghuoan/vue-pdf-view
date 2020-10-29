<template>
  <div class="pdf">
    <p class="arrow">
      <!-- 上一页 -->
      <span @click="changePdfPage(0)" class="turn" :class="{grey: currentPage==1}">上一页</span>
      {{currentPage}} / {{numPages}}
      <!-- 下一页 -->
      <span @click="changePdfPage(1)" class="turn" :class="{grey: currentPage==numPages}">下一页</span>
    </p>
    <pdf :src="src" :page="currentPage" @num-pages="numPages=$event" @page-loaded="currentPage=$event" @loaded="loadPdfHandler">
    </pdf>
  </div>
</template>

<script>
import pdf from 'vue-pdf'
export default {
  components: { pdf },
  data () {
    return {
      currentPage: 0, // pdf文件页码
      numPages: 0, // pdf文件总页数
      src: './git使用说明.pdf', // pdf文件地址
    }
  },
  created () {
    this.src = pdf.createLoadingTask(this.src)
  },
  methods: {
    // 改变PDF页码,val传过来区分上一页下一页的值,0上一页,1下一页
    changePdfPage (val) {
      // console.log(val)
      if (val === 0 && this.currentPage > 1) {
        this.currentPage--
      }
      if (val === 1 && this.currentPage < this.numPages) {
        this.currentPage++
      }
    },

    // pdf加载时
    loadPdfHandler (e) {
      this.currentPage = 1 // 加载的时候先加载第一页
    }

  }
}

</script>

<style scoped>
.turn {
  padding: 5px;
  background-color: skyblue;
  border-radius: 5px;
  color: #ffffff;
  cursor: pointer;
}
</style>
