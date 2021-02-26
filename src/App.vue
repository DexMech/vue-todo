<template>
  <div id="app">
    <div class=" column is-offset-one-quarter is-half">
      <div class="field">
        <label class="label">Digite a Tarefa</label>
        <div class="control">
          <input class="input" type="text" @keyup.enter="gerarTodo()" v-model="text">
        </div>
      </div>
    </div>
    <ul>
      <li v-for="todo in todos" :key="todo.id" @click="(e)=>marcarCompleto(e)">{{todo.text}}</li>
    </ul>
    <button @click="limparTodos()" class="button is-danger is-pulled-right">Limpar tudo</button>
  </div>
</template>

<script>



export default {
  data() {
    return {
      text: '',
      todos: []
    }
  },
  name: 'App',
  components: {
  
  },
  methods: {
    marcarCompleto(e) {
      const li = e.target
      console.log(li.classList)
      if(li.classList.contains('sublinhado')) {
        li.classList.remove('sublinhado')
      } else {
        e.target.classList.add('sublinhado')
      }
    },
    gerarTodo() {
      const id = Math.floor(Math.random() * 1000)
      const text = this.text
      this.todos.push({id, text})
      this.text = ''
    },
    limparTodos() {
      this.todos = []
    }
  }
  
}
</script>

<style>
.sublinhado {
  text-decoration: line-through;
  color: red;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
