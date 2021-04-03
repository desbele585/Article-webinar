<template>
  <div class="main-nav">
    <router-link :to="{name:'Home'}">Projects </router-link>
    <router-link :to="{name:'AddProject'}">Add New Projects</router-link>
  </div>

 
</template>

<script>
export default {

}
</script>

<style scoped>
.main-nav{
    text-align: center;
    margin: 40px auto;
}
.main-nav a{
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    font-size: 18px;
    color: #999;
}
a.router-link-active{
    border-bottom: 2px solid #00ce89;
    padding-bottom: 4px;
}
</style>