<script>
export default {
  data() {
    return {
      isEditing: false,
      ToDo: "",
      ToDos: [],
      selectedTodo: null,
    };
  },
  methods: {
    submitTodo() {
      this.ToDos.push(this.ToDo);
      this.ToDo = "";
    },
    removeTodo(index) {
      console.log(index);
      this.ToDos.splice(index, 1);
    },
    updateTodo() {
      this.ToDos.splice(this.selectedIndex, 1, this.ToDo);
      this.ToDo = "";
      this.isEditing = false;
    },
    editTodo(index, ToDo) {
      this.isEditing = true;
      this.ToDo = ToDo;
      this.selectedIndex = index;
    },
  },
};
</script>

<template>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"/>
<div class="wrapper">
    <header>TodoList Dika Remake</header>
<div v-if="!isEditing" >
    <div class="inputField">


      <input type="text" v-model="ToDo" placeholder="Masukkan ToDo" id="inputTodo">
      <button type="submit" value="add" @click="submitTodo"><i class="fas fa-plus"></i></button>


    </div>
</div>
<div v-else>
    <div class="inputField">
          <input type="text" v-model="ToDo"/>
          <button type="submit" value="update" @click="updateTodo">
            <i class="fas fa-check"></i>
          </button>
    </div>
</div>

<ul class="todoList">
     <li v-for="(ToDo, index) in ToDos">
     {{ ToDo }}
     <span class="icon" @click="removeTodo(index)"><i class="fas fa-trash"></i></span>
      <button class="btn btn-secondary mr-1 btn-space" @click="editTodo(index, ToDo)">
              Edit
            </button>
     </li>
    
    </ul>
    <div class="footer">
    
      <span class="pendingTasks">Masih Belajar</span>
    </div>
  </div>








</template>

