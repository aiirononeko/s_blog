<template>
  <el-col :span="8" style="margin-bottom: 35px;">
    <el-card class="box-card" style="margin: 0 auto;" shadow="hover">
      <div class="box-card-items" @click="$router.push(`/posts/${id}`)">
        <ul style="padding: 0;">
          <li v-for="(tag, i) in tags" :key="i" class="tag">{{ tag.fields.name }}</li>
        </ul>
        <h2 class="post-title">{{ title }}</h2>
        <p class="post-date">{{ getDate() }}</p>
        <lazy-component>
          <!-- classをバインディングすると警告でるの何でだろ -->
          <el-image :src="image.fields.file.url" :class="top-image">
            <div slot="placeholder" class="image-slot">
              Loading<span class="dot">...</span>
            </div>
          </el-image>
        </lazy-component>
      </div>
    </el-card>
  </el-col>
</template>

<script>
export default {
  props: {
    title: null,
    image: null,
    date: null,
    tags: null,
    id: null
  },
  methods: {
    getDate() {
      const date = new Date(this.date)
      const year = date.getFullYear()
      const month = date.getMonth() + 1
      const day = date.getDate()
      return year + '/' + month + '/' + day
    }
  }
}
</script>

<style scoped>
  .top-image {
    width: 295px;
    height: 176px;
  }

  .box-card {
    font-family: "M PLUS 1p";
    width: 350px;
    height: 405px;
  }

  .box-card-items {
    margin: auto;
  }

  .tag {
    list-style: none;
    text-align: center;
    font-size: 14px;
    margin-bottom: 20px;
    color: #696969;
  }

  .post-title {
    font-size: 16px;
    text-align: center;
    margin-bottom: 30px;
  }

  .post-date {
    font-size: 12px;
    text-align: center;
    margin-bottom: 15px;
    color: #808080;
  }
</style>
