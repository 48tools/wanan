<template>
  <img :src="src" alt="">
</template>

<script>
export default {
  props: ['src'],
  name: 'Avatar',
  data() {
    return {
      actualSrc: ''
    }
  },
  watch: {
    src() {
      this.updateSrc()
    }
  },
  methods: {
    async updateSrc() {
      const { src } = this
      const img = new Image()
      img.setAttribute('crossorigin', 'anonymous')
      const fr = new FileReader()

      img.onload = () => {
        fr.readAsDataURL(img)
      }
    }
  },
  mounted() {
    this.actualSrc = this.src
    this.updateSrc()
  }
}
</script>

<style scoped>

</style>
