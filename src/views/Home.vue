<template>
  <div class="home">
    <p>查看效果请：</p>
    <p>
      var img = new Image();
      document.body.appendChild(img)
      html2canvas(component.$refs.wanan.$el, { useCORS:true, scale: 2 }).then(function(canvas) {
      document.body.appendChild(canvas);
      img.src = canvas.toDataURL('image/jpeg', 1);
      });
    </p>
    <div class="wrapper y-scroll">
      <Wanan
        ref="wanan"
        :contents="contents"
        :topic="topic"
        :headImage="headImage"
        :showTopic="true"
        :footImage="footImage"
      ></Wanan>
    </div>
    <div class="display-area">
      <img :src="imgSrc" id="img-mount" alt="">
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import html2canvas from 'html2canvas'
import axios from 'axios'
import Wanan from '@/components/Wanan'
import contents from './contents'

console.log(axios)
window.html2canvas = html2canvas

export default {
  name: 'home',
  data() {
    return {
      contents,
      topic: '今晚要许的愿望',
      headImage: '/ctx.png',
      footImage: '/wxj.png',
      imgSrc: ''
    }
  },
  components: {
    Wanan
  },
  methods: {

  },
  mounted() {
    console.log(this)
    window.component = this
    console.log(html2canvas)
  }
}
</script>

<style lang="less">
  .wrapper {
    max-height: 800px;
  }
</style>
