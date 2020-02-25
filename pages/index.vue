<template>
  <el-container>
    <el-header>
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main style="margin-bottom: 50px;">
        <h2 class="posts-title">Posts</h2>
        <el-row>
          <Posts
            v-for="(post, i) in posts"
            :key="i"
            :title="post.fields.title"
            :image="post.fields.headerImage"
            :date="post.fields.publishDate"
            :tags="post.fields.tags"
            :id="post.sys.id"
          />
        </el-row>
      </el-main>
    </el-container>
    <el-footer>
      <Footer/>
    </el-footer>
  </el-container>
</template>

<script>
import client from '~/plugins/contentful'

import Header from '~/components/shared/Header'
import Posts from '~/components/top/Posts'
import Footer from '~/components/shared/Footer'
export default {
  components: {
    Header,
    Posts,
    Footer
  },
  asyncData({ env }) {
    return client
      .getEntries({ content_type: env.CTF_BLOG_POST_TYPE_ID })
      .then(entries => {
        return {
          posts: entries.items
        }
      })
      .catch(console.error)
  }
}
</script>

<style>
  .posts-title {
    text-align: center;
    margin: 80px 0;
  }

  @media screen and (max-width:480px) {
    .posts-title {
      margin: 30px 0;
      margin-bottom: 50px;
    }
  }
</style>
