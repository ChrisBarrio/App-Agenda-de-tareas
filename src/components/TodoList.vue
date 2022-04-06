
<template>
  <div class="task-list">
    <h2>{{tasks.length}} Tasks 📝</h2>
    <form class="form" @submit.prevent="createTask">
      <label class="label" for="task">Nueva tarea:</label>
      <input autofocus class="input" type="text" v-model="newTask" id="task" title="ingresar tarea" />
      <input class="button" type="submit" value="Crear tarea" title="agregar tarea" />
    </form>
    <ul class="list">
      <li
        class="task"
        v-for="(task, i) in tasks"
        :key="'task' + i"
        :class="{completed: task.completed}"
        @click="completeTask(task.text)"
        title="click para tachar"
      >{{task.text}}</li>
    </ul>
    <footer>Create by 
      <a 
      href="https://github.com/ChrisBarrio" 
      target="_blank" @mouseout="(estado = false)" @mouseover="(estado = true)" >Chris Barrio 👈🏽 <i 
      v-if="estado">👀</i></a>
    </footer>
  </div>
</template>

<script>
export default {
  data: () => ({
    newTask: "",
    tasks: [],
    estado: false
  }),
  methods: {
    createTask() {
      let task = {
        text: this.newTask,
        completed: false
      };
      this.tasks.push(task);
      this.newTask = "";
      
      console.log(this.tasks);
    },
    completeTask(taskText) {
      for (let i = 0; i < this.tasks.length; i++) {
        let task = this.tasks[i];
        if (taskText === task.text) {
          task.completed = !task.completed;
        }
      }
    }
  }
};


</script>
<style scoped>

.task-list {
  background-image: url('https://i.pinimg.com/736x/d7/5c/75/d75c75ddaf9b22b5bf309cae8ae0fd5f.jpg');
  background-repeat: none;
  background-size: cover;
  width: 800px;
  height: 100vh;
  max-width: 100%;
  margin: 0px auto;
  display:flex;
  flex-direction: column;
  align-items: center;  
}
h2{
  color: rgb(95, 95, 93);
}

.form {
  background: white;
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0px 10px 22px -1px rgba(239, 243, 239, 0.5);
  margin-top: 10px;
  background-attachment: fixed;
  position: relative;

}
.label {
  display: block;
  margin-bottom: 10px;
  font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
.input {
  height: 35px;
  border: none;
  background: rgb(235, 223, 223);
  border-radius: .4rem;
  font-size: .8rem;
}
.input:focus{
  background-color: rgb(46, 204, 113,0.2);
  text-transform: capitalize
}
.button {
  margin-left: 20px;
  padding: .6rem;
  height: 35px;
  border: none;
  border-radius: 5px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .2);
  background-color: #bcf5d4;
  color: #606263;
  cursor: pointer;
  font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  transition: all 1s;
}
.button:hover{
  border-radius: 1.4rem;
  transform: scale(0.8);
}
.list {
  margin-top: 40px;
  padding: 1rem;
  text-transform: capitalize;
  color: rgb(70, 67, 67);
  width: 15rem;
  height: 30rem;
  background-color: rgba(255, 255, 255, .15);  
  backdrop-filter: blur(5px);
  text-align: center;
}
.task {
  cursor: pointer;
  margin: 10px 0;
}
.completed {
  text-decoration: 1.5px line-through red;
  transition: all 1s;
  color: #ccc;
}
footer{
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: .6rem;
  width: 100%;
}
footer a{
  text-decoration: none;
  color: rgb(185, 155, 120);
  width: 100%;
}

</style>
