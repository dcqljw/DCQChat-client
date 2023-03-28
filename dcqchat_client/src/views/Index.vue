<template>
  <div>
    <el-input v-model="username" placeholder="Please input"/>
    <el-input v-model="room" placeholder="Please input"/>
    <el-input v-model="message" placeholder="Please input"/>
    <el-button type="primary" @click="join">join</el-button>
    <el-button type="primary" @click="send">send</el-button>
  </div>
</template>

<script>
import io from "socket.io-client"

export default {
  name: "IndexPage",
  data() {
    return {
      username: "",
      room: "",
      message: ""
    }
  },
  methods: {
    join() {
      console.log("123")
      this.socket = io("http://127.0.0.1:5000")
      this.socket.emit("join", {"username": this.username, "room": this.room})
    },
    send() {
      this.socket.emit("message", {"username": this.username, "room": this.room, "text": this.message})
    }
  }
}
</script>

<style scoped>

</style>