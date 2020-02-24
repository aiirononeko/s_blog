<template>
  <el-container>
    <el-header>
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main style="margin-bottom: 50px;">
        <el-alert
          title="お問い合わせを送信しました！"
          type="success"
          :class="{ showAlert: isActive }"
          show-icon>
        </el-alert>
        <h2 style="text-align: center; margin: 80px 0;">Contact to Excelsior</h2>
        <el-input type="text" placeholder="メールアドレス" style="margin-bottom: 30px;" v-model="email"></el-input>
        <el-input type="text" placeholder="お名前" style="margin-bottom: 30px;" v-model="name"></el-input>
        <el-input type="textarea" :rows="5" placeholder="お問い合わせ内容" style="margin-bottom: 30px;" v-model="body"></el-input>
        <el-button @click="submit">お問い合わせを送信する</el-button>
      </el-main>
    </el-container>
    <el-footer>
      <Footer/>
    </el-footer>
  </el-container>
</template>

<script>
  import { required, minLength, maxLength } from 'vuelidate/lib/validators'

  import Header from '~/components/shared/Header'
  export default {
    components: {
      Header
    },
    data() {
      return {
        email: '',
        name: '',
        body: '',
        isActive: true,
        count: 0
      }
    },
    validations: {
      email: {
        required,
        maxLength: maxLength(20)
      },
      name: {
        required,
        maxLength: maxLength(20)
      },
      body: {
        required,
        maxLength: maxLength(1000)
      }
    },
    methods: {
      submit() {
        // メール送信用のAPIをそのうち実装する
        if (this.count == 0) {
          this.isActive = false
          this.count++
          this.email = null
          this.name = null
          this.body = null
        } else {
          alert('お問い合わせは複数回送れません')
        }
      }
    }
  }
</script>

<style>
  .showAlert {
    display: none;
  }
</style>
