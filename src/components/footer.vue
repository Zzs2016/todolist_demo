<template>
    <div id="footer">
        <h5>{{ copyright }}</h5>
    </div>
</template>

<script>
export default {
    name:'app-footer',
    data(){
        return{
            copyright:"copyright@leonzhou"
        }
    }
}
</script>

<style scoped>
    #footer {
        height: 50px;
        width: 100%;
        position: absolute;
        bottom: 0px;
        left: 0px;
        background-color:grey;
    }
</style>
