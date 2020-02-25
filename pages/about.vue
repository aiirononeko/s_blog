<template>
  <el-container>
    <el-header>
      <Header/>
    </el-header>
    <el-container style="width: 80%; margin: 0 auto;">
      <el-main style="margin-bottom: 50px;">
        <h2 class="about-title">What is Excelsior?</h2>
        <el-row>

          <el-col :span="12" class="about-pc"><img src="~/assets/about-image.jpg" width="90%" height="90%" v-loading="loading"></el-col>
          <el-col :span="12" class="about-pc">
            <p class="about-message">
              Excelsior(エクセルシオール)とは、ラテン語で「気品のある」、あるいは「常に向上すること」を意味します。<br>
              美容を通じて常に向上し続けることを理想としている私の思いにちなんで、このブログタイトルは付けられました。<br>
              僕を含め、美容に関するコンプレックスを抱いている人は大勢いらっしゃいます。<br>
              このブログは、そういった方々が自身の悩みを解決する一助になれればという思いで綴っています。<br>
              僕と一緒に、常に向上し続け、気品のある美しい自分を目指していきませんか。
            </p>
          </el-col>

          <el-col :span="24" class="about-mobile"><img src="~/assets/about-image.jpg" width="100%" style="margin-top: 30px;" v-loading="loading"></el-col>
          <el-col :span="24" class="about-mobile">
            <p class="about-message">
              Excelsior(エクセルシオール)とは、ラテン語で「気品のある」、あるいは「常に向上すること」を意味します。<br>
              美容を通じて常に向上し続けることを理想としている私の思いにちなんで、このブログタイトルは付けられました。<br>
              僕を含め、美容に関するコンプレックスを抱いている人は大勢いらっしゃいます。<br>
              このブログは、そういった方々が自身の悩みを解決する一助になれればという思いで綴っています。<br>
              僕と一緒に、常に向上し続け、気品のある美しい自分を目指していきませんか。
            </p>
          </el-col>
        </el-row>

        <h2 class="about-title">Who is Hayato?</h2>
        <el-row>
          <el-col :span="12" class="about-pc">
            <p class="about-message2">
              申し遅れましたが、わたくし、「ハヤト」と申します。<br>
              中学生の頃から自分の肌やホクロ、シミに悩み続けていました。<br>
              当時から様々は化粧水やサプリメントを試しては研究し続ける毎日でした。<br>
              大学生になってからはアルバイトをしてお金を作り、顔にあるホクロの除去手術を行ったりもしました。<br>
              いわゆる「美容オタク」を続ける傍ら、日本化粧品検定の2級を取得するなどをしておりました。<br>
              現在は化粧品関係の会社に就職しており、日々美容の研究をしている、そんな22歳です。<br>
            </p>
          </el-col>
          <el-col :span="12" class="about-pc"><div style="background-color: gray; width: 500px; height: 500px; margin-left: 30px;"></div></el-col>

          <el-col :span="24" class="about-mobile"><div class="about-profile"></div></el-col>
          <el-col :span="24" class="about-mobile">
            <p class="about-message2">
              申し遅れましたが、わたくし、「ハヤト」と申します。<br>
              中学生の頃から自分の肌やホクロ、シミに悩み続けていました。<br>
              当時から様々は化粧水やサプリメントを試しては研究し続ける毎日でした。<br>
              大学生になってからはアルバイトをしてお金を作り、顔にあるホクロの除去手術を行ったりもしました。<br>
              いわゆる「美容オタク」を続ける傍ら、日本化粧品検定の2級を取得するなどをしておりました。<br>
              現在は化粧品関係の会社に就職しており、日々美容の研究をしている、そんな22歳です。<br>
            </p>
          </el-col>
        </el-row>
        <h2 class="about-title" style="margin-bottom: 60px; margin-top: 60px;">Let's Read My Posts!</h2>
          <el-row>
            <el-col :span="3" v-for="(tag, i) in tags" :key="i" class="about-pc">
              <el-button round>{{ tag.fields.name }}</el-button>
            </el-col>
            <el-col :span="24" v-for="(tag, i) in tags" :key="i" class="about-mobile">
              <el-button round style="margin-bottom:20px;">{{ tag.fields.name }}</el-button>
            </el-col>
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
  import Footer from '~/components/shared/Footer'
  export default {
    components: {
      Header,
      Footer
    },
    asyncData({ env }) {
    return client
      .getEntries({ content_type: 'tag' })
      .then(entries => {
        return {
          tags: entries.items
        }
      })
      .catch(console.error)
  }
  }
</script>

<style>
  .about-title {
    text-align: center;
    margin: 80px 0;
  }

  .about-mobile {
    display: none;
  }

  .about-message {
    margin-left: 50px;
    margin-top: 10px;
    line-height: 45px;
    letter-spacing: 3px;
  }

  .about-message2 {
    margin-right: 50px;
    margin-top: 10px;
    line-height: 45px;
    letter-spacing: 3px;
  }

  .about-profile {
    background-color: gray;
    width: 500px;
    height: 500px;
    margin-left: 30px;
  }

  @media screen and (max-width:480px) {
    .about-title {
      margin: 30px 0;
    }

    .about-pc {
      display: none;
    }

    .about-mobile {
      display: grid;
    }

    .about-message {
      margin-left: 10px;
      margin-top: 30px;
      line-height: 50px;
      letter-spacing: 1px;
    }

    .about-message2 {
      margin-right: 0px;
      margin-top: 0;
      line-height: 50px;
      letter-spacing: 1px;
    }

    .about-profile {
      background-color: gray;
      width: 250px;
      height: 250px;
      margin: 30px auto;
      margin-bottom: 30px;
    }
  }
</style>
