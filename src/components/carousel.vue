<template>
  <div class="carousel">
    <div class="posts" :style="computed_left">
      <div class="postbox" v-for="(w,id) in works" :class="{cur_item: id==now_index}">
        <div class="cover" :style="bg_css(w.cover)">
          <div class="infos">
            <h1>{{w.title}}</h1>
            <h5>{{w.description}}</h5>
          </div>
        </div>
      </div>
    </div>
    <div class="control_left" @click="delta(-1)">
      <i class="fa fa-angle-left" aria-hidden="true"></i>
    </div>
    <div class="control_right" @click="delta(1)">
      <i class="fa fa-angle-right" aria-hidden="true"></i>
    </div>
  </div>
</template>

<script>
var works = [
  {
    title: '海象樂園',
    description: '趴在冰層上的懶惰動物',
    cover: 'https://unsplash.it/400/300?image=1084'
  },
  {
    title: '搭船遊去',
    description: '不會游泳只好搭船',
    cover: 'https://unsplash.it/400/300?image=1083'
  },
  {
    title: '老年學鋼琴',
    description: '學習永遠不嫌晚！',
    cover: 'https://unsplash.it/400/300?image=1082'
  },
  {
    title: '高樓的一隅',
    description: '繁複的幾何線條構築',
    cover: 'https://unsplash.it/400/300?image=1081'
  },
  {
    title: '草莓來襲',
    description: '聽見果農的艱辛',
    cover: 'https://unsplash.it/400/300?image=1080'
  },
  {
    title: '探索宇宙',
    description: '看見光的速度與殘影',
    cover: 'https://unsplash.it/400/300?image=1079'
  }
]
export default {
  name: 'carousel',
  data () {
    return {
      now_index: 0,
      works: works,
      span: 1430
    }
  },
  methods: {
    bg_css: function (url) {
      return {
        'background-image': 'url(' + url + ')'
      }
    },
    delta: function (d) {
      // (原本的id+變化+總長）% 總長
      // (0 + (-1) + 5) % 5 = 4
      this.now_index = (this.now_index + d + this.works.length) % this.works.length
    }
  },
  computed: {
    computed_left () {
      return {
        'left': (-this.span * this.now_index) + 'px'
        //  左距離＝偏移負的單格距離＊現在正在瀏覽的index
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../scss/main.scss';
</style>
