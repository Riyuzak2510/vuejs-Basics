<template>
  <div id="app" class="container">
    <h1 class="text-center"> {{title}} </h1>
    <div class="card">
      <div class="card-body text-center">
      <form @submit.prevent = "addTodo">
        <input v-model="newTodo" type="text" name="newTodo" id="newTodo">
        <button type="submit" name="button" class="btn btn-primary text-center">Add</button>
        <button @click="allDone" type="button" name="button" class="btn btn-success text-center">All Done</button>
      </form>
      </div>
    </div>
    <div class="text-left">
      <ul>
        <template v-for="todo in todos">
          <li :key="todo.id">
              <div class="input-group">
                  <div class="input-group-prepend ">
                    <div class="input-group-text card  mb-3">
                      <input type="checkbox" aria-label="Checkbox for following text input" v-model="todo.done">
                    </div>
                  </div>
                  <div class="card mb-3" style="width: 26rem;">
                    <div class="card-body text-center">
                      <div :class="{done: todo.done}">{{todo.title}}</div>
                    </div>
                    <div class="card-body text-center">
                      <button @click="removeTodo(todo)" name="button" class="btn btn-danger">Remove</button>
                    </div>
                  </div>
              </div>   
          </li>
        </template>
      </ul>
    </div>
  </div>
</template>


<script>
export default {
  name: 'app',
  data () {
    return {
      title : 'Todo List',
      newTodo: '',
      todos : []
    }
  },
  methods : {
    addTodo(){
     if(this.newTodo != "")
     {
        this.todos.push({
        title: this.newTodo,
        done: false
      })
      this.newTodo=""
     }
    },
    removeTodo(todo){
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex,1)
    },
    allDone() {
      this.todos.forEach(todo => {
        todo.done = true;
      })
    }
  }
}
</script>

<style>
.done{
      text-decoration: line-through;
     }
</style>
