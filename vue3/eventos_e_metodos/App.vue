<template>
  <div>
    <H1>minha lista de tarefas</H1>
    <button @click="handleshowhidelist" >ver lista</button>
    <br>
    <input type="text" @keyup.enter="addTask" v-model="state.currentTask">

    <ul v-if="state.showlist">
      <li v-for="task  in state.tasks" v-bind:key="task"> {{task.name}} 
        <button @click="remove(task)">&times;</button></li>       
    </ul>  
    <p v-else>tarefas ocultas</p>
  </div>
</template>

<script>
import {reactive} from 'vue'

export default {

setup(){
  const state  = reactive ({
      showlist:false,
      tasks:[
          {name:"fazer o curso",isdone:false}   
          ]
  })
    function handleshowhidelist(){
      state.showlist = !state.showlist
    }

    function addTask(){
      state.tasks.push({
        name: state.currentTask,
        isdone:false
      })
      state.currentTask=''
    }

    function remove (task){
      state.tasks = state.tasks.filter(t=>t.name !==task.name)
    }


  return{   state ,handleshowhidelist,addTask,remove }
}
}

</script>

<style>

</style>
