<template>
  <div>
    <img id="main" :src="image" @click="switchImage"
    @mousedown="onMouseDown"/>
    <pre>{{console}}</pre>
  </div>
</template>

<script>
export default {
  props: {
    image: Object
  },
  data() {
    return {
      current: 1,
      console: ""
    }
  },
  methods: {
    switchImage() {
      if (this.current == 1) {
        this.current = 2
      } else {
        this.current = 1
      }
      this.setImage()
    },
    onMouseDown(e) {
      this.consoleLog(`${e.offsetX}, ${e.offsetY}`)
    },
    setImage() {
      if (this.current == 1) {
        this.image = require('@/assets/kari1.png')
      } else {
        this.image = require('@/assets/kari2.png')
      }
    },
    consoleLog(msg) {
      this.console = `${msg}\n${this.console}`
    }
  },
  created() {
    this.setImage()
  }
}
</script>
