<template>
  <div class="hello">
    <div>
      {{title}}
    </div>
    <hr>
    <button @click="convert">点击获取数据</button>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',
    data() {
      return {
        title: "静态数据"
      }
    },
    //在这里调用ajax请求方法
    created(){
      this.convert();
    },
    methods: {
      convert: function () {
        axios.get("api/sysUser/getSomething").then(res => {
          this.title = res.data;
        })
      }
    }
  }
</script>