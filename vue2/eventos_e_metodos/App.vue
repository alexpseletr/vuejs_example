<template>
  <div>
    <H1>minha lista de tarefas</H1>
    <button @click="handleshowhidelist" >ver lista</button>
    <br>
    <input type="text" @keyup.enter="addTask" v-model="currentTask">

    <ul v-if="showlist">
      <li v-for="task  in tasks" v-bind:key="task"> {{task.name}} 
        <button @click="remove(task)">&times;</button></li>       
    </ul>  
    <p v-else>tarefas ocultas</p>
  </div>
</template>

<script>

export default {
  data:() =>({
    showlist:false,
    tasks:[
        {name:"fazer o curso",isdone:false}   
        ]
  }),
  methods:{
    handleshowhidelist(){
      this.showlist = !this.showlist
    },
    addTask(){
      this.tasks.push({
        name: this.currentTask,
        isdone:false
      })
      this.currentTask=''
    },
    remove (task){
      this.tasks = this.tasks.filter(t=>t.name !==task.name)
    }

  }
}
</script>


