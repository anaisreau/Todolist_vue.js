<template>
<div class="content">
    To Do List Vue.js 
    <div>
        <br/>
        <input class='input' type="text" placeholder="enter your task here" v-model="newTask" @keyup.enter="addTask">
        
    </div><br/>
            <a v-for="task in tasks" :key="task.id" class="task" :class="{completed : task.completed}">   
            <div class="todos">   
            <input type="checkbox" v-model="task.completed" class="toggle">
            <label>{{ task.title }}</label>
            </div>    
            </a>
        </div>


</template>



<style>
.completed {
  color: green;
  font-style: italic;
  width: 80%;
  margin: auto;
}

.content{
    font-size: 2em;
    }

.todos{
    text-align: left;
    margin-left: 30%;
    }

.toggle{
    margin-right: 1.5em;
    width:30px;
	height:30px;
    }

.input{
    width:40%;
    font-size : 1em
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