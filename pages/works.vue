<template>
  <div>
    <h2>Works</h2>
    <ul class="works">
      <li v-for="item in works" :key="item.title">
        <a :href="item.url" target="_blank">
          <dl>
            <dt><h3>{{ item.title }}</h3></dt>
            <dd class="detail">{{ item.detail }}</dd>
            <dd class="tools">Tools: {{ toolsList(item.tools) }}</dd>
            <dd class="date">{{ item.date }}</dd>
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
        {
          title: 'Preshare',
          detail: 'あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ',
          tools: ['Vue.js', 'Firebase'],
          url: 'https://google.com',
          date: '2018/11'
        },
        {
          title: 'This page',
          detail: 'ポートフォリオサイト',
          tools: ['Vue.js', 'Nuxt.js'],
          url: '/',
          date: '2018/10'
        },
        {
          title: 'Resister Calendar',
          detail: 'Vanilla JavaScriptでVMMVパターンで設計しました。',
          tools: ['Vanilla JavaScript'],
          url: 'https://google.com',
          date: '2018/10'
        },
        {
          title: 'Movie Carousel',
          detail: 'YoutubeIframeAPIを利用した動画入りカルーセルです。',
          tools: ['jQuery', 'YoutubeIframeAPI'],
          url: 'https://google.com',
          date: '2017/12'
        },
        {
          title: 'Modal',
          detail: '選択したDOMから情報を取得してモーダル上に表示させています。',
          tools: ['jQuery'],
          url: 'https://google.com',
          date: '2018/6'
        },
        {
          title: 'Usage tools by Vue.js',
          detail: '個人用Web給与明細確認ツール。ローカルに保存していたWeb給与明細のページをiframeに表示させます。サイドナビから見たい年月を選択して表示している明細情報を変更できます。初めてVue.jsに触れた時に練習で作りました。',
          tools: ['Vue.js'],
          date: '2018/3'
        },
        {
          title: 'Develop tool by jQuery',
          detail: '同一性ポリシーを利用してiframe内のページを別タブで開く際にHTMLを操作して当てるスタイルシートを変更できます。',
          tools: ['jQuery'],
          date: '2017/3'
        },
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
$mainColor: #ecf4f3; // rgb(236, 244, 243)
$subColor: #76dbd1; // rgb(118, 219, 209)
$sub2Color: #57a99a; // rgb(87, 169, 154)
$sub3Color: #555151;

.works {
  margin-top: 15px;
}

.works > li {
  background-color: rgba(236, 244, 243, .8);
  transition: all .2s ease-out;
  &:hover {
    background-color: rgba(118, 219, 209, .8);
  }
}

.works > li + li {
  margin-top: 10px;
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

.tools {
  font-size: 75%;
}

.date {
  font-size: 70%;
}
</style>
