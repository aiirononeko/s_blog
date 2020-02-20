<template>
  <el-container>
    <el-header>
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main style="margin-bottom: 50px;">
        <h2 style="text-align: center; margin: 40px 0;">Contact Me!</h2>
      </el-main>
    </el-container>
    <el-footer>
      <Footer/>
    </el-footer>
  </el-container>
</template>

<script>
  import Header from '~/components/shared/Header'
  export default {
    components: {
      Header
    }
  }
</script>
