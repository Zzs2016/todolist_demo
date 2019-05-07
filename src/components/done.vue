<template>
    <div class="doneThing">
        <br>
        <h1>DoneList</h1>
        <ul >
            <li id="dongsomething" v-for='(value,index) in doneThing' :key=index>
            ({{ index+1 }}){{ value.time }}&nbsp;&nbsp;&nbsp;{{ value.thing }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:["doneThing","list"],
    data(){
        return{

        }
    },
    
    methods:{

    }
}
</script>

<style scoped>
    ul{
        padding-inline-start: 0px;
    }
    .doneThing {
        width: 400px;
        margin: 0 auto;
        margin-top: 10px;
    }
    #dongsomething {
        display: inline-block;
        height: 32px;
        width: 400px;
        line-height: 32px;
        text-align: left;
        padding-left: 1em;
        margin-bottom: 10px;
        -webkit-box-shadow: 3px 3px 3px rgba(0,0,0,0.5);
        -moz-box-shadow: 3px 3px 3px rgba(0,0,0,0.5);
        border-radius: 3px;
        list-style-type: none;
        background-color:#fff;
        overflow: auto;
    }
</style>