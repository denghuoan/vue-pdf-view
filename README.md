# 在vue中预览pdf

## vue-pdf

### 安装[vue-pdf](https://www.npmjs.com/package/vue-pdf)

```bash
npm install --save vue-pdf
// 
yarn add vue-pdf
```

### 使用

#### 不分页

```vue
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

```

#### 分页

```vue
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
```

## pdfjs

### 下载

[pdf js 官网](https://mozilla.github.io/pdf.js/getting_started/#download)

### 使用

#### 将下载后的文件放到服务器上

如: http://192.168.0.26:9999/pdfView/

```vue
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
```

#### 将下载后的文件放到public文件里

```vue
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
```



 # 仓库

- gitee: https://gitee.com/denghuoan/vue-pdf-view
- github: https://github.com/denghuoan/vue-pdf-view

- csdn博文: https://blog.csdn.net/denghuocc/article/details/109361877

