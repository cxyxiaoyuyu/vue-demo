<template>
  <div class="child">
    <h4>我是子组件</h4> 
    <div>这是来自父组件的title: <b>{{ title }}</b></div>
    <button @click="sendMsgToParent">点我向父组件传递信息</button>
    <button @click="sendMsgByBus">点我通过事件总线向父组件传递信息</button>
  </div>
</template>

<script>
  export default {
    props: ['title'],
    methods: {
      sendMsgToParent(){
        this.$emit('getMsg','我是来自子组件的信息')
      },
      sendMsgByBus(){
        this.$bus.$emit('getMsgByBus','我是通过事件总线传递的信息')
      }
    }
  }
</script>

<style scoped>
.child {
  border: 1px solid blue;
  margin-bottom: 20px;
  padding-bottom: 20px;
}
div {
  margin-bottom: 20px;
}
</style>