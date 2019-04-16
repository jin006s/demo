<template>
  <div class="hello">
    <h1>
      <span>{{this.$store.state.count}}</span> ---- <span>{{this.$store.getters.computedCount}}</span>
    </h1>
    <!-- <button @click="incCount()">增加数量+</button> -->
    <el-button type="primary" @click="incCount()">增加数量</el-button>
  </div>
</template>

<script>
  import request from '../request'
  import store from '@/vuex/store.js'

  export default {
    name: 'HelloWorld',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    //挂载Store
    store,
    created(){
      console.log(this,'this')
      request({
        method:'get',
        url:'/cover/list',
        data:{
          appId:26
        }
      }).then(res=>{
        console.log(res)
      })
    },
    methods:{
            incCount(){
                //改变vuex store里面的数据
                this.$store.commit('incCount');   /*触发 mutations 改变 state里面的数据*/
                // this.$store.dispatch('incMutationsCount');   /*触发 actions里面的方法   */
            }
        }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scope>
  //1.外部引入方式
  //末尾需要加分号
  @import './test.scss';
  $highlight-color: red;
  //2.内嵌样式
  h1{
    span{
      color:$highlight-color;
    }
  }

</style>
