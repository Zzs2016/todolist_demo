<template>
    <div class="todo">
        <select id="selectTime" v-model="currentTime" required>  
        <option value="" selected>选择时间</option>
        <option v-for='item in timeList' :key=item.id>{{ item }}</option>
        </select>
        <input id="doSomething" type="text" v-model="currentSomething" required="required" placeholder="do something..."/><button @click="add">提交</button>  
        <br>
        <h1>ToDoList</h1>
        <ul>
            <li id="something" v-for='(value,index) in list' :key=index >
            ({{ index+1 }}){{ value.time }}&nbsp;&nbsp;&nbsp;{{ value.thing }}
            <button id="update" @click="update(index)">完成</button>
            </li>
        <!-- <li v-for=' in list' ></li> -->
        </ul>  
    </div>
</template>

<script>
export default {
    props:['addSomething','selectTime','list','timeList','doneThing'],
    // name: 'todo'
    data(){
        return{
            currentSomething: this.addSomething,
            currentTime: this.selectTime
            }
        },
    methods:{
        add:function(){

            if(this.currentTime == "" && this.currentSomething == ""){
                alert("Select Time & Input Something!")
            }
            else if(this.currentTime == ""){
                alert("Select Time!")
            }
            else if(this.currentSomething == "" ){
                alert("Input Something!")
            }
            else{
                // alert('startpush');
                this.list.push({time: this.currentTime, thing: this.currentSomething});
                this.currentSomething='';
                this.currentTime=""
                // alert('finishpush');
            }
        },
        update:function(index){
        //1.赋给完成事项
            // alert('startupdate');
            // this.doneThing.push(this.list[index])
            this.$emit("childUpdate",this.list[index])
            //2.移除待办事项
            this.list.splice(index,1)
            // console.log(this.list)
            alert('Well Done!')
        },
    }   
}
</script>
<style scoped>
    .todo {
        width: 400px;
        margin: 0 auto;
    }
    button {
        height: 32px;
        margin-left: 5px;
        margin-right: 5px;
        border-radius: 3px;
        background-color: #fff;
    }
    ul {
        padding-inline-start: 0px;
    }
    #update {
        float: right;
    }
    #selectTime {
        height: 32px;
        border-radius: 3px;
    }
    #doSomething {
        height: 25px;
        border-radius: 3px;
    }
    #something {
        display: inline-block;
        height: 34px;
        width: 400px;
        line-height: 34px;
        text-align: left;
        padding-left: 1em;
        margin-bottom: 10px;
        list-style-type: none;
        border-radius: 3px;
        -webkit-box-shadow: 3px 3px 3px rgba(0,0,0,0.5);
        -moz-box-shadow: 3px 3px 3px rgba(0,0,0,0.5);
        background-color:#fff;
        overflow: auto;
  
}
    
</style>