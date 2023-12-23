<template>
  <div class="container">
    <div class="greating">
      <h1>{{message}}</h1>
      <form @submit.prevent> 
        <input type="text" v-model="username" placeholder="Username">
        <input type="email" v-model="email" placeholder="Email">
        <input type="password" v-model="password" placeholder="Password">
        <p id="pass" style="visibility:hidden;">Password length should be at least 8 symbols</p>
        <button @click="register" >Register</button>
      </form>
      
      <h2>Registred users</h2>
      <div class="list">
        <li v-for="user in users">
          <p>Username: <span>{{user.usern}}</span></p>
          <p>Email: <span>{{user.usere}}</span></p>
          <p>Password: <span>{{user.userp}}</span></p>
          <button @click="remove(user.id)">Remove</button>
        </li>
      </div>
    </div>
  </div>
  <div class="container">
    <div class="greating">
      <h1>Task Add FORM</h1>
      <form @submit.prevent> 
        <input type="text" v-model="task" placeholder="Task">
        <button @click="addTask" >Add</button>
      </form>
      
      <h2>LIST OF TASKS</h2>
      <div class="list">
        <li v-for="task in tasks">
          <p>Task</p>
          <p><span>{{task.text}}</span></p>
          <p>Process: <span>
            <p v-if="task.done" style="width: 50px;">DONE</p>
            <p v-else style="width: 50px;">process.</p>
          </span></p>
          <button @click="task.done = !task.done" v-if="task.done" style="background: red;">Reset</button>
          <button @click="task.done = !task.done" v-else style="background: green;">Done</button>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
  export default{
    data(){
      return{
            message: "Hello, This is Assignment 11 done by 220107099",
            users: [
              { 
                id: 1,
                usern: "Mukhammed",
                usere: "220107099@stu.sdu.edu.kz",
                userp: "123456qwerty"
              }
            ],
            username: '',
            email:'',
            password:'',
            tasks: [{
              id: 1,
              text: "Do homework",
              done: false
            }],
            task: ''
      }
    },
    methods:{
      register(){
        if(this.password.length >= 8){
          const user = {
          id: Date.now(),
          usern: this.username,
          usere: this.email,
          userp: this.password
          }
          this.users.push(user);
          this.username = "";
          this.password = "";
          this.email = "";
          const pass = document.getElementById("pass");
          pass.style.visibility = "hidden";
        }else{
          const pass = document.getElementById("pass");
          pass.style.visibility = "visible";
        }
      },
      remove(id){
        this.users = this.users.filter(user => user.id != id);
        return
      },
      addTask(){
        const task = {
          id: Date.now(),
          text: this.task,
          done: false
        }
        this.tasks.push(task);
        this.task = "";
      },
      changed(task){
        task.done = !task.done;
      }
    },
  }
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container{
  padding: 10px 10%;
}
h1{
  text-align: center;
}
form{
  display: flex;
  flex-direction: column;
}
input{
  widows: 100%;
  padding: 10px 15px;
  margin-top: 20px;
  border-radius: 10px;
  border: 1px solid teal;
}
.list{
  display: flex;
  gap: 15px;
}
h2{
  margin: 15px 10px
}
p{
  font-size: 15px;
  font-weight: 600;
  display: flex;
  gap: 20px;
}
button{
  padding: 10px 20px;
  margin-top: 20px;
  align-self: flex-end;
  color: teal;
  border: 1px solid teal;
  border-radius: 10px;
  font-size: 16px;
  font-weight: 600;
}
li{
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: flex-start;
  border: 1px solid teal;
  padding: 15px;
}
.checking{
  padding: 0;
  margin: 0;
}
</style>
