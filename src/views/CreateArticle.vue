<template>
 <el-form @submit.native.prevent='saveAticle' :model="article" ref="form" label-width="90px" class="demo-ruleForm">
  <el-form-item label="文章标题" prop="name">
    <el-input v-model="article.title"></el-input>
  </el-form-item>

  <el-form-item label="文章内容" prop="desc">
    <el-input type="textarea" v-model="article.body"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" native-type='submit'>立即创建</el-button>
    <el-button @click="resetForm('ruleForm')">取消</el-button>
  </el-form-item>
 </el-form>
</template>


<script>
  export default {
    data() {
      return {
        article: {
          
        },
      };
    },
    methods: {
      saveAticle() {
        this.$http.post('articles', this.article).then(res => {
          this.$message({
            message: '文章创建成功',
            type: 'success'
          })
          this.$router.push('/articles/index')
        })
      }
    }
  }
</script>