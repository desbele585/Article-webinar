<template>
  <div class="project">
     <div class="actions"> 
        <h3 @click="showDetail=!showDetail">{{project.title}}</h3> 
        <div class="icons">
            <span class="material-icons delete" @click="deleteProject">delete</span>
             <span class="material-icons tick">done</span>
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
       }
   }

}
</script>

<style>
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
</style>