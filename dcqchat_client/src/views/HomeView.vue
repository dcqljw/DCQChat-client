<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <el-button type="primary">Primary</el-button>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import io from "socket.io-client"

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  methods: {
    data() {
      this.socket = io("http://127.0.0.1:5000")
      this.socket.emit("join", {"username": "dcq", "room": "A"})

    }
  }
}
</script>
