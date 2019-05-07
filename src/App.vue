<template>
  <div id="app">
    <app-header></app-header>
    <todo :addSomething="addSomething"
          :selectTime="selectTime"
          :list="list"  
          :timeList="timeList"  
           
          @childUpdate='parentUpdate'
          
            >
    </todo>
    <done :doneThing="doneThing"         
            >  
    </done>
    <app-footer></app-footer>
  </div>
</template>

<script>
import todo from './components/todo';
import done from './components/done';
export default {
  name: 'App',
  components: {
    todo,
    done
  },
  data(){
    return{
      addSomething:"",
      selectTime:"",
      list:[],
      timeList:['8:00-9:00','9:00-10:00','10:00-11:00','11:00-12:00','12:00-13:00'],
      doneThing:[]
      
    }
  },
  methods:{
    // parentAdd(){
    //   this.$refs['add'].add()
    // },
    parentUpdate: function(list){
        // console.log(doneThing)
        this.doneThing.push(list)
        // console.log(this.list)
    },
    // parentSort: function(){
      
    // }
        
  }
}
</script>

<style scoped>
    html,body {
      margin: 0;
      padding: 0;
      height: 100%;
      background: #ccc;
    }
    #app {
      position: relative;
      width: 100%;
      min-height: 100%;
      height: auto !important;
      height: 100%;
      padding-bottom: 50px;
      margin:0 auto;
      text-align: center;
      background: #ccc;
      box-sizing: border-box;
      overflow: hidden;
    }

</style>
