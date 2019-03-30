<template>
<div id='app'>
    <div id='nav'>
        <Header />
    </div>
    <router-view/>
</div>
</template>

<script>
import Header from "./components/layout/Header.vue";

export default {
    name: 'App',
    components:{
        Header
    }
}
</script>



<style>
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;

}
body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
}
.btn{
    display: inline-block;
    border: none;
}
</style>

