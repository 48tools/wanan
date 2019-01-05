<template>
  <div :class="['wanan-container', theme, className]">
    <div class="wanan-header" v-if="headImage || topicPlacement === 'top'">
      <img :src="headImage" class="wanan-header-image" alt="" v-if="headImage">
      <h2 class="topic-title top-topic-name" v-if="topicPlacement === 'top'">
        <span class="hashtag">#</span>{{topic}}<span class="hashtag">#</span>
      </h2>
    </div>
    <ul class="contents">
      <li class="wanan-item flex align-top" v-for="(item) in contents" :key="item.message + item.add_time">
        <img crossOrigin="anonymous" class="sender-avatar" :src="getAvatar(item.from_qq)" alt="">
        <div class="wanan-content cell">
          <div class="wanan-content-header flex align-center">
            <h4 class="wanan-sender ellipsis cell" v-text="item.nick_name"></h4>
            <span class="create-time" v-text="getSendTime(item.add_time)"></span>
          </div>
          <p class="wanan-text" v-html="formatContent(item.message)"></p>
        </div>
      </li>
    </ul>
    <div class="wanan-footer" v-if="footImage || topicPlacement === 'foot'">
      <img :src="footImage" class="wanan-footer-image" alt="" v-if="footImage">
      <h2 class="topic-title foot-topic-name" v-if="topicPlacement === 'top'">
        <span class="hashtag">#</span>{{topic}}<span class="hashtag">#</span>
      </h2>
    </div>
  </div>
</template>

<script>
import { formatDate } from '../../utils/format-date'

export default {
  props: {
    topic: {
      type: String,
      required: true
    },
    headImage: String,
    footImage: String,
    customStyles: String,
    className: String,
    contents: {
      type: Array,
      required: true
    },
    theme: String,
    showTopic: {
      type: Boolean,
      default: true
    },
    topicPlacement: {
      type: String,
      default: 'none'
    }
  },
  name: 'Wanan',
  computed: {
    topicRegex() {
      return new RegExp(`#[^#]*${this.topic}[^#]*#`, 'i')
    }
  },
  methods: {
    formatContent(text) {
      const hashtag = '<span class="hashtag">#</span>'
      const full = `${hashtag}<span class="topic">${this.topic}</span>${hashtag}`

      return text.replace(this.topicRegex, this.showTopic ? full : '').trim()
    },
    getAvatar(qq) {
      return `http://qlogo.lovelyctx.com/g?b=qq&s=160&nk=${qq}`
      // return `http://q2.qlogo.cn/headimg_dl?bs=${qq}&dst_uin=${qq}&spec=160&url_enc=0&referer=bu_interface&term_type=PC`
      // return 'http://wx.qlogo.cn/mmopen/vi_32/RnLIHfXibgFHlticiclzflpriaLsC3TS9b2Sbj05Wh3vGlhcFutt18dfkXGUt8x11e4q2KHlX4EHHaBb6XylLQW1kQ/0'
    },
    getSendTime(timestamp) {
      return formatDate(timestamp, 'hh:ss')
    }
  }

}
</script>

<style lang="less">
@import "./style";
</style>
