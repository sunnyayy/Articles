<template>
  <el-form @submit.prevent="saveArticle" ref="form" :model="article" label-width="120px">
    <el-form-item label="文章标题">
      <el-input v-model="article.title"></el-input>
    </el-form-item>
    <el-form-item label="文章内容">
      <el-input type="textarea" v-model="article.body"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" native-type="submit">立即创建</el-button>
      <el-button>取消</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
export default {
  data() {
    return {
      article: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    saveArticle() {
      this.$axios.post("/articles", this.article).then(res => {
        this.$message({
          message: '文章创建成功~',
          type: 'success'
        });
        this.$router.push('/articles/index')
      })
      
      console.log(this.article);
    }
  }
}
</script>