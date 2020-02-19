<template>
  <header>
    <el-row :gutter="20">
      <el-col :span="3"><h1 class="blog-title">Excelsior</h1></el-col>
      <el-col :span="3" :offset="11"><nuxt-link to="/">Excelsiorについて</nuxt-link></el-col>
      <el-col :span="2"><nuxt-link to="/">Contact</nuxt-link></el-col>
      <el-col :span="3"><el-button icon="el-icon-search" circle style="margin-top: 10px;"></el-button></el-col>
    </el-row>
  </header>
</template>

<style>
  header {
    width: 100%;
    background-color: #fff;
  }

  .blog-title {
    font-size: 30px;
    line-height: 60px;
    margin-left: 230px;
  }

  a {
    text-decoration: none;
    color: #000;
    line-height: 60px;
    font-weight: bold;
    font-size: 15px;
  }
</style>
