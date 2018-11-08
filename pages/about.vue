<template>
  <div class="about">
    <h2>About me</h2>
    <ul class="profiles">
      <li v-for="item in profiles" :key="item.title">
        <dl>
          <dt>{{ item.title }}</dt>
          <dd>{{ item.detail }}</dd>
        </dl>
      </li>
    </ul>
    <div class="skills" :class="{ open: isActive_skill }">
      <h3><span @click="isActive_skill=!isActive_skill">Skill<span class="toggleBtn"></span></span></h3>
      <ul>
        <li v-for="item in skills" :key="item.title">
          <dl>
            <dt>{{ item.title }}</dt>
            <dd :data-level="item.level"><span :style="levelStyle(item.level)"></span></dd>
            <dd v-show="isActive_skill" class="detail" v-html="item.detail">{{ item.detail }}></dd>
          </dl>
        </li>
      </ul>
    </div>
    <div class="careers" :class="{ open: isActive_career }">
      <h3><span @click="isActive_career=!isActive_career">Career<span class="toggleBtn"></span></span></h3>
      <ul>
        <li v-for="item in careers" :key="item.title">
          <dl>
            <dt><span>{{ item.start }}</span> ~ <span>{{ item.end }}</span> {{ item.title }}</dt>
            <dd v-show="isActive_career" class="detail" v-html="item.detail"></dd>
          </dl>
        </li>
      </ul>
    </div>
    <!-- <ul class="sections">
      <li v-for="item in sections" :key="item.title">
        <h4>{{ item.title }}</h4>
        <p v-html="item.detail"></p>
      </li>
    </ul> -->
  </div>
</template>


<script>
var profiles = [
  { title: 'Name', detail: 'Junta Muramatsu' },
  // { title: 'Birthday', detail: '1993/1/24' },
  { title: 'Job', detail: 'Frontend Engineer' },
  { title: 'Location', detail: 'Tokyo' }
]
var skills = [
  { level: 90, title: 'HTML/HTML5',
  },
  { level: 90, title: 'EJS',
  },
  { level: 50, title: 'pug',
  },
  { level: 90, title: 'CSS/CSS3',
  },
  { level: 70, title: 'Sass(scss)',
  },
  { level: 70, title: 'Stylus',
  },
  { level: 80, title: 'JavaScript(ES5, ES6)',
  },
  { level: 80, title: 'jQuery',
  },
  { level: 40, title: 'Vue.js',
    detail: `プライベートで勉強中`
  },
  { level: 30, title: 'Nuxt.js',
    detail: `同上`
  },
  { level: 15, title: 'React',
    detail: `チュートリアルレベル 実務で既存コードを編集`
  },
  { level: 8, title: 'Angular',
    detail: `チュートリアルレベル`
  },
  { level: 30, title: 'Three.js',
    detail: ``
  },
  { level: 70, title: 'Youtube Iframe API',
    detail: ``
  },
  { level: 65, title: 'Web performance',
    detail: ``
  },
  { level: 70, title: 'Visual Studio Code',
    detail: `Atom, SublimeText3`
  },
  { level: 60, title: 'Photoshop',
    detail: ``
  },
  { level: 66, title: '色彩',
    detail: `色彩検定2級を保持`
  },
  { level: 8, title: 'AWS',
    detail: `S3で静的サイトを公開`
  },
  { level: 5, title: 'Python',
    detail: `<a href="https://www.oreilly.co.jp/books/9784873117782/" target="_blank">退屈なことはPythonにやらせよう（O\'Reilly）</a>読書中`
  },
]
var careers = [
  {
    start: '2016/11',
    end: '',
    title: 'SES',
    detail: `大規模飲食系BtoBサービスを展開している企業に常駐。飲食店向けホームページ作成サービスのフロントエンドを担当。業務内容はサービスのエンハンス・リファクタリング。<br/>担当制作例: 予約管理カレンダー・YouTube動画を組み込み可能なカルーセル・汎用モーダルウィンドウ・複数静的ページ管理画面<br/>特筆事項: 機能制作のほかに、<a href="https://www.oreilly.co.jp/books/9784873115658/" target="_blank">リーダブルコード</a>を参考にして数千行リファクタリングを行った経験。`
  },
  {
    start: '2016/5',
    end: '',
    title: 'Lei Hau\'oli Co.,Ltd.',
    detail: `中規模受託WEB制作会社にフロントエンドエンジニアとして所属。社内でJavaScript研修を受けた後、小中規模の静的サイトの制作などを担う。<br/>制作例: 大手化粧品メーカーコーポレートサイト...`
  },
  {
    start: '2016/1',
    end: '2016/5',
    title: 'In preparation',
    detail: `休職。JavaScriptを勉強するためMacBookProと本を購入。<br/>参考にしていた本:
<a href="https://www.oreilly.co.jp/books/9784873115733/" target="_blank">JavaScript第6版</a>・
<a href="https://www.oreilly.co.jp/books/9784873113913/" target="_blank">JavaScript: The Good Parts</a>・
<a href="https://www.oreilly.co.jp/books/9784873116211/" target="_blank">開眼! JavaScript</a>・
<a href="https://www.oreilly.co.jp/books/9784873114880/" target="_blank">JavaScriptパターン</a>・
<a href="https://www.amazon.co.jp/Web%E5%88%B6%E4%BD%9C%E8%80%85%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AECSS%E8%A8%AD%E8%A8%88%E3%81%AE%E6%95%99%E7%A7%91%E6%9B%B8-%E3%83%A2%E3%83%80%E3%83%B3Web%E9%96%8B%E7%99%BA%E3%81%AB%E6%AC%A0%E3%81%8B%E3%81%9B%E3%81%AA%E3%81%84%E3%80%8C%E4%BF%AE%E6%AD%A3%E3%81%97%E3%82%84%E3%81%99%E3%81%84CSS%E3%80%8D%E3%81%AE%E8%A8%AD%E8%A8%88%E6%89%8B%E6%B3%95-%E8%B0%B7-%E6%8B%93%E6%A8%B9/dp/4844336355" target="_blank">Web制作者のためのCSS設計の教科書</a>・
<a href="https://www.oreilly.co.jp/books/9784873115658/" target="_blank">リーダブルコード</a><br/>
勉強会で知り合った人の企業から内定をもらう。`
  },
  {
    start: '2015/4',
    end: '2015/12',
    title: 'Dawn.Inc',
    detail: `小規模受託WEB制作会社に新卒入社。マークアップエンジニアとして所属。HTML/CSSでのコーディングをひたすら行う。業務内容はLPサイト制作や小規模コーポレートサイトのWordPress組み込みなど。社内で浸透していなかったSassの導入を提案。上京を機に外部の勉強会に積極的に参加するようになる。より技術的に成長できる環境を求め退職。`
  },
  {
    start: '2011/4',
    end: '2015/3',
    title: 'University of Aizu',
    detail: `コンピュータ理工学部卒。学部3年次にJavaScriptに興味を持ち、ドットインストールで独学する。4年次にWebGL(Three.js)を用いた大学構内ストリートビューを作成。デザインに興味があり色彩検定2級を取得。絵を描く趣味のおかげでPhotoshopの操作を覚える。フロントエンドエンジニアを志し、Web制作の基礎を作る思いでマークアップエンジニアとして内定をもらう。`
  },
];

export default {
  data() {
    return {
      isActive_skill: false,
      isActive_career: false,
      profiles: profiles,
      skills: skills,
      careers: careers
    }
  },
  methods: {
    levelStyle (level) {
      return { 'width': this.isActive_skill ? `${level}%` : 0 }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/global.scss';

.profiles {
  margin-top: .5em;
  li + li {
    margin-top: .5em;
  }
  dl {
    display: flex;
    align-items: baseline;
  }
  dt {
    white-space: nowrap;
    &:after {
      content: ':';
      display: inline-block;
      margin-right: .5em;
    }
  }
}

.toggleBtn {
  display: inline-block;
  position: relative;
  vertical-align: middle;
  margin-left: .2em;
  &::before,
  &::after {
    content: '';
    display: block;
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto;
    border-top: 2px solid $subColor;
    width: 10px;
  }
  &::before {
    display: block;
    transform: rotate(90deg)
  }
  .open &::before {
    display: none;
  }
}

.skills,
.careers {
  margin-top: .5em;
  line-height: 1.5;
  h3 {
    span {
      cursor: pointer;
    }
  }
  > ul {
    margin-top: .5em;
  }
  &.open {
    li {
      + li {
        margin-top: .5em;
      }
    }
  }
  .detail {
    font-size: .75em;
  }
}

.skills {
  li {
    display: inline-block;
    &:not(:last-child)::after {
      content: ', ';
      display: inline-block;
      white-space: pre-wrap;
    }
  }
  dl {
    display: inline-block;
  }
  &.open {
    li {
      display: block;
      &::after {
        display: none;
      }
    }
    dl {
      display: block;
    }
  }
}
[data-level] {
  position: relative;
  width: 100%;
  height: 0;
  background-color: $mainColor;
  span {
    display: inline-block;
    position: absolute;
    width: 0;
    height: 100%;
    background-color: $subColor;
    transition: all 1s ease;
  }
  .open & {
    height: 3px;
  }
}

.careers {
  dt {
    span {
      display: inline-block;
      width: 3.7em;
      &:first-child {
        text-align: right;
      }
    }
  }
  &.open {
    dd {
      margin-top: .3em;
    }
  }
  .detail {
    padding: .75em;
    background-color: $mainColor;
  }
}

.sections {
  margin-top: .5em;
}
</style>
<style lang="scss">
.about {
  a {
    text-decoration: underline;
    &:hover {
      text-decoration: none;
    }
  }
}
</style>
