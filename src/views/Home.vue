<template>
  <div class="parent">
    <h4>我是父组件</h4>
    <child :title="title" @getMsg="getMsgFromChild"></child>
    <div>子组件向我传递的消息： <b>{{ msgFromChild }}</b></div>
  </div>
</template>

<script>
// @ is an alias to /src
import child from '@/components/child.vue'

export default {
  data(){
    return {
      title: '我是来自父组件的title',
      msgFromChild: '',
    }
  },
  mounted(){
    this.$bus.$on('getMsgByBus',(msg)=>{
      this.msgFromChild = msg
    })
  },
  methods: {
    getMsgFromChild(msg){
      this.msgFromChild = msg
    }
  },
  components: {
    child
  }
}
</script>

<style>
.parent {
  border: 1px solid red;
}
</style>
