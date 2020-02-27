<template>
  <header>
    <el-row :gutter="20">
      <el-col :span="3"><nuxt-link to="/" class="blog-title">Excelsior</nuxt-link></el-col>
      <el-col :span="3" :offset="12" class="header-link"><nuxt-link to="/about">Excelsiorについて</nuxt-link></el-col>
      <el-col :span="2" class="header-link2"><nuxt-link to="/contact">Contact</nuxt-link></el-col>
      <el-col :span="3" class="header-link3"><el-button icon="el-icon-search" circle style="margin-top: 10px;" @click="dialogVisible = true"></el-button></el-col>
      <el-dialog
        title="タグで検索する"
        :visible.sync="dialogVisible"
        width="30%"
      >
        <ul>
          <li v-for="(tag, i) in tags" :key="i">{{ tag.fields.name }}</li>
        </ul>
        <span slot="footer" class="dialog-footer">
          <el-button type="primary" @click="dialogVisible = false">Search</el-button>
        </span>
      </el-dialog>
    </el-row>
  </header>
</template>

<script>
  export default {
    data() {
      return {
        dialogVisible: false
      }
    }
  }
</script>

<style>

  /* ノートPC用スタイル */
  header {
    width: 100%;
    background-color: #fff;
  }

  .blog-title {
    font-size: 30px;
    line-height: 60px;
    margin-left: 180px;
  }

  a {
    text-decoration: none;
    color: #000;
    line-height: 60px;
    font-weight: bold;
    font-size: 15px;
  }

  /* スマホ用スタイル */
  @media screen and (max-width:480px) {
    header {
      height: 30px;
    }

    .blog-title {
      font-size: 18px;
      margin-left: 20px;
    }

    a {
      line-height: 30px;
      font-size: 10px;
    }

    .header-link {
      width: 130px;
      margin-top: 17px;
      margin-left: 100px;
    }

    .header-link2 {
      margin-top: 17px;
    }

    .header-link3 {
      display: none;
    }
  }

  /* デスクトップPC用スタイル */
  @media screen and (min-width:781px) {
    
  }
</style>
