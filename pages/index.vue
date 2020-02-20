<template>
  <el-container>
    <el-header>
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main>
        <h2 style="text-align: center; margin: 40px 0;">New Posts</h2>
        <el-row>
          <Posts
            v-for="(post, i) in posts"
            :key="i"
            :title="post.fields.title"
            :image="post.fields.headerImage"
            :date="post.fields.publishDate"
            :tags="post.fields.tags"
          />
        </el-row>
        <h2 style="text-align: center; margin: 40px 0;">Popular Tags</h2>
        <Tags
        />
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
import Tags from '~/components/shared/Tags'
import Footer from '~/components/shared/Footer'
export default {
  components: {
    Header,
    Posts,
    Tags,
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
