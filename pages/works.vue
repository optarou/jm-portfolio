<template>
  <div>
    <h2>Works</h2>
    <ul class="works">
      <li v-for="item in works" :key="item.title" ontouchstart="">
        <a :href="item.url" target="_blank">
          <dl>
            <dt><h3>{{ item.title }}</h3></dt>
            <dd class="detail">{{ item.detail }}</dd>
            <dd class="tools">Tools: {{ toolsList(item.tools) }}</dd>
            <dd class="date">{{ item.date }}</dd>
            <dd class="capture" :style="{ backgroundImage: 'url(' + require(`@/assets/image/${item.capture}`) + ')' }" v-if="item.capture"></dd>
          </dl>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      works: [
        // {
        //   title: 'Preshare',
        //   detail: 'あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ',
        //   capture: '',
        //   tools: ['Vue.js', 'Firebase'],
        //   url: 'https://google.com',
        //   date: '2018/11'
        // },
        {
          title: 'J.M.Portfolio',
          detail: 'ポートフォリオサイト',
          capture: 'work1.png',
          tools: ['Vue.js', 'Nuxt.js'],
          url: '/',
          date: '2018/11'
        },
        // {
        //   title: 'Resister Calendar',
        //   detail: 'Vanilla JavaScriptでVMMVパターンで設計しました。',
        //   capture: '',
        //   tools: ['Vanilla JavaScript'],
        //   url: 'https://google.com',
        //   date: '2018/10'
        // },
        // {
        //   title: 'Movie Carousel',
        //   detail: 'YoutubeIframeAPIを利用した動画入りカルーセルです。',
        //   capture: '',
        //   tools: ['jQuery', 'YoutubeIframeAPI', 'File API'],
        //   url: 'https://google.com',
        //   date: '2017/12'
        // },
        // {
        //   title: 'Modal',
        //   detail: '選択したDOMから情報を取得してモーダル上に表示させています。',
        //   capture: '',
        //   tools: ['jQuery'],
        //   url: 'https://google.com',
        //   date: '2018/6'
        // },
        // {
        //   title: 'Usage tools by Vue.js',
        //   detail: '個人用Web給与明細確認ツール。ローカルに保存していたWeb給与明細のページをiframeに表示させます。サイドナビから見たい年月を選択して表示している明細情報を変更できます。初めてVue.jsに触れた時に練習で作りました。',
        //   capture: '',
        //   tools: ['Vue.js'],
        //   date: '2018/3'
        // },
        // {
        //   title: 'Develop tool by jQuery',
        //   detail: '同一性ポリシーを利用してiframe内のページを別タブで開く際にHTMLを操作して当てるスタイルシートを変更できます。',
        //   capture: '',
        //   tools: ['jQuery'],
        //   date: '2017/3'
        // },
      ]
    }
  },
  methods: {
    toolsList (list) {
      return list.join(', ')
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/global.scss';

.works {
  margin-top: 15px;
  > li {
    background-color: rgba(236, 244, 243, .8);
    transition: all .2s ease-out;
    &:hover {
      background-color: rgba(118, 219, 209, .8);
      .capture {
        opacity: .8;
      }
    }
    + li {
      margin-top: 10px;
    }
  }
}

dl {
  padding: 10px;
}

dd {
  margin-top: 5px;
}

.detail {
  font-size: 80%;
  line-height: 1.4;
}

.capture {
  width: 100%;
  height: 100px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  transform: translateZ(0);
  transition: all .2s ease-out;
}

.tools {
  font-size: 75%;
}

.date {
  font-size: 70%;
}
</style>
