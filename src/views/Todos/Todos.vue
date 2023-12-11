<template>
    <h1>Todos list</h1>

    <ul>
        <li v-for="todo in todos" :key="todo.identify">
            {{ todo.name }}
        </li>
    </ul>
</template>

<script>
export default {
    name: 'TodosVue',
    setup() {
        const todos = [
            {identify: 1, name: 'tarefa 01', completed: true},
            {identify: 2, name: 'tarefa 02', completed: false},
            {identify: 3, name: 'tarefa 03', completed: true},
        ]

        const name = ref('default value')

        name.value = 'teste 2'
        
        return {
            todos,
            name
        }
    }
}
</script>

<style lang="scss" scoped>
    
</style>