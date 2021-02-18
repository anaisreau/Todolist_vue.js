<template>
<div>
    To Do List Vue.js 
    <div>
        <input type="text" placeholder="enter your task here" v-model="newTask" @keyup.enter="addTask">
    </div>
            <a v-for="task in tasks" :key="task.id" class="tasks" :class="{completed : task.completed}">   
            <div>   
            <input type="checkbox" v-model="task.completed" class="toggle">
            <label>{{ task.title }}</label>
            </div>    
            </a>
        </div>


</template>



<style>
.completed {
  color: green;
  background: black;
  width: 80%;
  margin: auto;
}

</style>


<script>
export default {
    name : "todoList",
    data() {
       
        return {
            newTask : "",
            idTask : 2,
            tasks : [{
                "id" : 1 , 
                "title" : "first test",
                "completed" : false
}
            ]
            }
},


methods:{
    addTask() {
        this.tasks.push({
        id : this.idTask,
        title : this.newTask,
        completed : false 
    })

this.newTask = "",
this.idTask++
    
}, 

}
}

</script>