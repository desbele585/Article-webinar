<template>
  <div class="project" :class="{complete:project.complete}">
     <div class="actions"> 
      
        <h3 @click="showDetail=!showDetail">{{project.title}}</h3> 
        <div class="icons">
            <router-link :to="{name:'EditProject', params:{id:project.id}}">
            <span class="material-icons">edit</span>
            </router-link>
            <span class="material-icons delete" @click="deleteProject">delete</span>
             <span class="material-icons tick" @click="handleComplete">done</span>
        </div> 
     </div>
     <div class="details" v-if="showDetail">
         <p>{{project.details}}</p>
     </div>
  </div>
</template>

<script>
export default {
   props:['project'],
   data(){
       return{
             showDetail:false,
             url:'http://localhost:3000/projects/' + this.project.id
       }
   },
   methods:{
       deleteProject(){
           fetch(this.url,{method:'DELETE'})
             .then(()=> this.$emit('delete', this.project.id))
            .catch(err=>console.log(err.message))
       },
       handleComplete(){
           fetch(this.url,{
               method:'PATCH',
               headers:{'Content-Type':'application/json'},
               body:JSON.stringify({complete:!this.project.complete})
           })
           .then(()=>{
               this.$emit('complete',this.project.id)
           })
       }
   }

}
</script>

<style scoped>
.project{
    width: 100%;
    height:  100%;
    margin:20px auto;
    background: white;
    padding: 10px 20px;
    border-radius: 4px;
    box-shadow: 1px 2px 3px rgba(0,0,0,0.05);
    border-left: 4px solid #e90074;
}
h3{
    cursor: pointer;
}
.actions{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.material-icons{
    font-size: 24px;
    margin-left: 10px;
    color: #bbb;
    cursor: pointer;
}
.material-icons:hover{
    color: #777;
}
.project.complete{
    border-left: 4px solid #00ce89;
}
.project.complete .tick{
    color: #00ce89;
}
.delete{
    color: red;
}
</style>>