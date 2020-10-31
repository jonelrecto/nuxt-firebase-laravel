<template>
  <div>
    <h2>this is also with folder users with {{$route.params.id}}</h2>
    <ul v-for="(todo, i) in todos" :key="i">
      <li>{{todo.desc}}</li>
      <button @click="updateTodo(todo, i)" ></button>
    </ul>

    <input type="text" v-model="toUpdateDesc" />
    <button @click="save" ></button>
  </div>
</template>
<script>
export default {
  data () {
    return {
      toUpdateTodo: {},
      toUpdateDesc: '',
      todos: [
        { desc: 'hehe', isDone: false },
        { desc: 'g', isDone: false },
        { desc: 'ss', isDone: false },
        { desc: 'tt', isDone: false }
      ]
    }
  },
  methods: {
    updateTodo (todo, index) {
      // console.log(todo, index,' todo')
      this.toUpdateDesc = todo.desc
      this.toUpdateTodo = { ...todo, index}
    },
    save() {
      console.log(this.toUpdateTodo, this.toUpdateDesc, 'asf')
      let desc = this.toUpdateDesc
      
      this.todos[this.toUpdateTodo.index] = { desc: this.toUpdateDesc, isDone: this.toUpdateTodo.isDone }
      console.log(this.todos)
      this.$forceUpdate()
    }
  }
}
</script>