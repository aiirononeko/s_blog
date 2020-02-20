<template>
  <el-container>
    <el-header style="margin-bottom: 50px;">
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main style="margin-bottom: 50px; background-color: #fff;">
        <div class="container">
          <ul style="padding: 0; margin-top: 50px;">
            <li v-for="(tag, i) in post.fields.tags" :key="i" class="tag">{{ tag.fields.name }}</li>
          </ul>
          <h1 style="margin: 40px 0; font-size: 38px;">{{ post.fields.title }}</h1>
          <p class="date">{{ getDate(post.fields.publishDate) }}</p>
          <el-image :src="post.fields.headerImage.fields.file.url" style="margin-bottom: 50px;">
            <div slot="placeholder" class="image-slot">
              Loading<span class="dot">...</span>
            </div>
          </el-image>
          <hr style="margin-bottom: 50px;">
          <div v-html="toHtmlString(post.fields.body)" style="margin-bottom: 50px;"></div>
          <hr style="margin-bottom: 50px;">
        </div>
      </el-main>
    </el-container>
    <el-footer>
      <Footer/>
    </el-footer>
  </el-container>
</template>

<script>
import client from '~/plugins/contentful.js'
import { BLOCKS } from '@contentful/rich-text-types';
import { documentToHtmlString } from "@contentful/rich-text-html-renderer";

import Header from '~/components/shared/Header'
import Footer from '~/components/shared/Footer'

export default {
  components: {
    Header,
    Footer
  },
  methods: {
    getDate(d) {
      const date = new Date(d)
      const year = date.getFullYear()
      const month = date.getMonth() + 1
      const day = date.getDate()
      return year + '/' + month + '/' + day
    },
    toHtmlString(obj) {
      return documentToHtmlString(obj)
    }
  },
  asyncData({ env, params }) {
    return client
      .getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        'sys.id': params.id
      })
      .then(entries => {
        console.log(entries.items[0])
        return {
          post: entries.items[0]
        }
      })
      .catch(console.error)
  }
}
</script>

<style scoped>
  .container {
    width: 65%;
    margin: 0 auto;
  }

  .tag {
    list-style: none;
    font-size: 20px;
    margin-bottom: 20px;
    color: #696969;
  }

  .date {
    font-size: 14px;
    margin-bottom: 50px;
    color: #808080;
  }
</style>
