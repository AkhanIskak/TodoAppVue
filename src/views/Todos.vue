<template>
  <div >  
         <h2>Todo application</h2>
        <AddTodo
        @add-todo='addTodo'/>
        <hr>
        <select v-model='filter'>
           <option value='all'>all</option>
           <option value='completed '>completed</option>
           <option value='not-completed'>not-comleted</option>
        </select>
       <AppCont 
       v-if='filteredTodos.length'
       v-bind:todos="filteredTodos"
       @remove-todo="removeTodo"
        />
        <p v-else>No todos</p>
        <hr>
<router-link to='/'>Home </router-link>
         
  </div>
</template>
               
<script>

import AppCont from '../components/AppCont.vue'
import AddTodo from'../components/AddTodo.vue'
                                         
                             
export default {

  name: "App",
 
  data(){
    return{ 
      todos:[ 
      {id:1,title:"buy bread ",completed:false},
      {id:2,title:"buy milk ",completed:false},
      {id:3,title:"buy butter ",completed:false},
      {id:4,title:"buy people ",completed:false},

      ],
      filter:[]
    }
  },
   mounted(){
 
},
computed :{
filteredTodos(){
  if(this.filter==='all'){
    
    return this.todos
  }else if (this.filter==='completed'){

    return this.todos.filter(x=>x.completed)
  }
  else {
   
     return this.todos.filter(x=>!x.completed)
  }
}


},
  components: {
    AppCont,
    AddTodo
  },
  methods:{
 removeTodo(id){
   this.todos = this.todos.filter(t=>t.id!==id);
 },
 addTodo(todo){
this.todos.push(todo)

 }
  }
};
</script>
