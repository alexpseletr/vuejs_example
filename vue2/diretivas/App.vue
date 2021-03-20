<template>
  <div>
    <H1>minha lista de tarefas</H1>
    <button @click="() => showlist = !showlist" >ver lista</button>
    <br>
    
    <ul v-if="showlist">
      <li v-for="task  in tasks" v-bind:key="task"> {{task.name}} </li>  
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
  })
}
</script>

<style>

</style>
