<template>
  <nav class="filter-nav">
      <button
     @click="update('all')" :class="{active:current==='all'}">View All</button>
      <button
     @click="update('completed')" :class="{active:current==='complete'}" >Completed</button>
      <button
     @click="update('ongoing')" :class="{active:current==='ongoing'}" >Ongoing</button>
  </nav>
</template>

<script>
export default {
 props:['current'],
methods:{
    update(by){
        this.$emit('filterChange',by)
    }
}
}
</script>

<style>
.filter-nav button{
    background:none;
    border: none;
    color: #bbb;
    outline: none;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    letter-spacing: 1px;
    font-weight: bold;
    cursor: pointer;
}
.filter-nav button.active {
 color:  black;
}
</style>