<template>
  <div>
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
            <dd v-show="isActive_skill" class="detail">{{ item.detail }}</dd>
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
            <dd v-show="isActive_career" class="detail">{{ item.detail }}</dd>
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
  { title: 'Birthday', detail: '1993/1/24' },
  { title: 'Job', detail: 'Frontend Engineer' }
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
    detail: 'プライベートで勉強中'
  },
  { level: 30, title: 'Nuxt.js',
    detail: '同上'
  },
  { level: 15, title: 'React',
    detail: 'チュートリアルレベル 実務で既存コードを編集'
  },
  { level: 8, title: 'Angular',
    detail: 'チュートリアルレベル'
  },
  { level: 30, title: 'Three.js',
    detail: ''
  },
  { level: 70, title: 'Youtube Iframe API',
    detail: ''
  },
  { level: 60, title: 'Web performance',
    detail: ''
  },
  { level: 70, title: 'Visual Studio Code',
    detail: '<- Atom <- Sublime3'
  },
  { level: 8, title: 'AWS',
    detail: 'S3で静的サイトを公開'
  },
  { level: 5, title: 'Python',
    detail: '退屈なことはPythonにやらせよう（O\'Reilly）読書中'
  },
]
var careers = [
  {
    start: '2016/11',
    end: '',
    title: 'SES',
    detail: `詳細`
    // detail: `大規模飲食系BtoBサービスのHP作成サービスのエンハンス業務を現在まで行なっています。`
  },
  {
    start: '2016/5',
    end: '',
    title: 'Lei Hau\'oli Co.,Ltd.',
    detail: `詳細`
    // detail: `フロントエンドエンジニアフロントエンドエンジニアフロントエンドエンジニアフロントエンドエンジニアフロントエンドエンジニア 中規模Webサイト作成`
  },
  {
    start: '2016/1',
    end: '2016/5',
    title: 'In preparation',
    detail: `詳細`
    // detail: `サイ本などを購入してJavaScriptを勉強していましたサイ本などを購入してJavaScriptを勉強していましたサイ本などを購入してJavaScriptを勉強していましたサイ本などを購入してJavaScriptを勉強していました`
  },
  {
    start: '2015/4',
    end: '2015/12',
    title: 'Dawn.Inc',
    detail: `詳細`
    // detail: `マークアップエンジニア
    // LP/小規模Webサイト作成小規模Webサイト作成小規模Webサイト作成小規模Webサイト作成小規模Webサイト作成
    // WordPress実装`
  },
  {
    start: '2011/4',
    end: '2015/3',
    title: 'University of Aizu',
    detail: `詳細`
    // detail: `コンピュータ理工学部`
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
