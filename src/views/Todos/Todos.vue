
<template>
    <h1>
        Lista de Tarefas
        <router-link :to="{name:'todos.create'}">+</router-link>
    </h1>

    <div v-show="loading">
        Carregando as tarefas
    </div>

    <ul>
        <li v-for="todo in todos" :key="todo.identify">
            <todo :todo="todo" @todoDeleted="removeTodoList"/>
        </li>
    </ul>
</template>

<script>
import { onMounted, ref} from 'vue'

import TodoService from '@/services/todos.services'
import Todo from './Todo.vue'

export default {
    name: 'TodosVue',
    setup() {
        const todos = ref([])

        const loading = ref(false)

        onMounted (() => { 
            loading.value = true

            TodoService.getAll()
                    .then(response =>  todos.value = response.data.data)
                    .catch(error => console.log(error))
                    .finally(() => loading.value = false)
          })

          const removeTodoList = (todo) => todos.value.splice(todos.value.indexOf(todo), 1)

          return {
            loading,
            todos,
            removeTodoList,
          }
    },
    component: {
        Todo
    }
}
</script>

<style lang="scss" scoped>
    
</style>