<template>
  <div>
    <h1>To Do List</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Add task" />
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <span :class="{ done: task.completed }" @click="toggleTask(index)">{{
          task.text
        }}</span>
        <button @click="removeTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: this.loadTasks(),
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = "";
        this.saveTasks();
      }
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
      this.saveTasks();
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
      this.saveTasks();
    },

    saveTasks() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },

    loadTasks() {
      const savedTasks = localStorage.getItem("tasks");
      return savedTasks ? JSON.parse(savedTasks) : [];
    },
  },
};
</script>

<style scoped>
body {
  background-color: #f4f4f4;
}

h1 {
  color: #333;
  font-family: monospace;
}

input {
  padding: 10px;
  margin: 10px 0;
  width: 300px;
  border: 2px solid #a76f6f;
  border-radius: 5px;
  outline: none;
  transition: border-color 0.3s;
}

input:focus {
  border-color: #697565;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background: #fff;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin: 5px 0;
  transition: background 0.3s;
  max-width: 400px;
}

li:hover {
  background: #f0f8ff;
}

.done {
  text-decoration: line-through;
  color: #aaa;
}

button {
  background-color: #dc3545;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px 10px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #c82333;
}
</style>
