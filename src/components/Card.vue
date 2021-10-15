<template >
    <v-card :class="`card ${ mark } my-3 ` ">
        <!-- Card Title -->
        <v-card-title>{{ title }}</v-card-title>

        <!-- Card Text -->
        <v-card-text>
            <div class="text">
                {{ description }}
            </div>
            <div class="time">Time for do it : {{ time }}</div>
        </v-card-text>

        <!-- Card Actions -->
        <v-card-actions dir="rtl">
            <v-btn class="primary  mx-4" @click="deletTodo(id)">donne</v-btn>
        </v-card-actions>
    </v-card>
</template>
<script>
export default {
    data() {
        return {
            Todos: JSON.parse(localStorage.getItem("Todos")),
            Todo: "",
        }
    },
    props: [
        "title",
        "description",
        "time",
        "mark",
        "id"
    ],
    methods: {
        deletTodo(id){
            let NewTodos = this.Todos.filter(todo => todo.id != id)
            localStorage.setItem('Todos', JSON.stringify(NewTodos))
        }
    },
}
</script>
