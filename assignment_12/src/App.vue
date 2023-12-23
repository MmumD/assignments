<!-- HTML -->
<template>
  
  <div class="container">
    <div class="tasks">
      <div class="title">
        <h1>Task List <span>{Task 1}</span></h1>
        <h2>Incomplited tasks: {{incompleteTasks}}</h2>
        <h2>Complited tasks: {{completedTasks}}</h2>
        
      </div>
      <div class="addFrom">
        <form @submit.prevent>
          <input type="text" placeholder="Task" v-model="task.title">
          <button @click="addTask">Add</button>
        </form>
      </div>
      <div class="">
        <h1>Incomplited</h1>
        <div class="allTasks">
          <div class="task" v-for="task in incompleteTaskList">
          <p><span>Title: </span>{{task.title}}</p>
          <p><span>Status: </span>{{task.status == false ? "in process...":"done"}}</p>
          <div class="btn">
            <button @click="process(task)">{{task.status == false ? "Done":"in process..."}}</button>
            <button style="border: 1px solid black; background: red; color: black;" @click="deleteTask(task.id)">Delete</button>
          </div>
          </div>
        </div>
        <h1>Complited</h1>
        <div class="allTasks">
          <div class="task" v-for="task in completedTaskList">
            <p><span>Title: </span>{{task.title}}</p>
            <p><span>Status: </span>{{task.status == false ? "in process...":"done"}}</p>
            <div class="btn">
              <button @click="process(task)">{{task.status == false ? "Done":"in process..."}}</button>
              <button style="border: 1px solid black; background: red; color: black;" @click="deleteTask(task.id)">Delete</button>
          </div>
        </div>
        </div>
      </div>
    </div>
    <div class="userProfile">
      
    </div>
  </div>
</template>

<!-- JS -->

<script>
  export default{
    computed: {
    incompleteTasks() {
      return this.taskList.filter(task => !task.status).length;
    },
    completedTasks() {
      return this.taskList.filter(task => task.status).length;
    },
    incompleteTaskList() {
      return this.taskList.filter(task => !task.status);
    },
    completedTaskList() {
      return this.taskList.filter(task => task.status);
    }
  },
    data(){
      return {
        task:{
          title:"",
          status:false,
        },
        taskList:[
          {id: 0, title: "Do homework", status: false},
          {id: 1, title: "Do Assignment", status: false}
        ]
      }
    },
    methods:{
      addTask(){
        const task = {
          id: Date.now(),
          title: this.task.title,
          status: false,
        }
        this.taskList.push(task);
        this.task.title = "";
      },
      process(task){
        task.status = !task.status;
      },
      deleteTask(id){
        this.taskList = this.taskList.filter(task => task.id != id);
        return
      }
    }
  }
</script>
<!-- CSS -->
<style>
.container{
  padding: 10px 10%;
}
.title{
  text-align: center;
  color: teal;
}
.tasks{
  display: flex;
  flex-direction: column;
}
.addFrom form{
  display: flex;
  gap: 15px;
}
.addFrom input{
  width: 100%;
  padding: 10px 15px;
  font-size: 18px;
  border-radius: 15px;
  border: 1px solid teal;
  color: teal;
  font-weight: 400;
}
.addFrom button{
  padding: 10px 15px;
  border: 1px solid teal;
  font-size: 18px;
  font-weight: 600;
  border-radius: 15px;
  background: #fff;
  color: teal;
}
.allTasks{
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  padding-top: 50px;
}
.task{
  word-break: break-all;
  border: 1px solid teal;
  padding: 10px 15px;
  border-radius: 10px;
  color: teal;
  width: 200px;
}
.task p span{
  font-weight: 600;
}
.task p{
  font-weight: 500;
}
.btn{
  display: flex;
  justify-content: space-between;
}
.btn button{
  color: teal;
  background: #fff;
  padding: 10px 15px;
  border: 1px solid teal;
  font-size: 16px;
  border-radius: 15px;

}
</style>
