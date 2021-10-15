<template>
    <div>
        <!-- success Snackbar -->
        <v-snackbar v-model="UsSnackbar" color="success" top :timeout="4000">
            <span>Awesome! You Add a new Todo. </span>
            <v-btn text  color="white" @click="UsSnackbar=false" class="ml-4"><v-icon>mdi-window-close</v-icon></v-btn>
        </v-snackbar>
        <v-card class="my-3">
            <v-container>
                <v-form class="form">
                    <h2 class="secondary--text">Add new Todo :</h2>
                    <v-text-field label="Title" v-model="title"></v-text-field>
                    <v-textarea label="Description" v-model="description"></v-textarea>
                    <v-time-picker format="ampm" full-width v-model="time"></v-time-picker>
                    <v-select :items="items" label="Mark" v-model="mark"></v-select>
                    <v-btn block color="primary" class="mt-6" @click="addTodo()">Add Todo</v-btn>
                </v-form>
            </v-container>
        </v-card>    
    </div>
</template>

<script>
export default {
    data() {
        return {
            title:"",
            description:"",
            time:"",
            data:"",
            mark:"Null",
            items:["M-Blue", "M-Red", "M-Green", "M-Yallow"],
            Todos: JSON.parse(localStorage.getItem("Todos")),
            conter: localStorage.getItem("conter"),
            UsSnackbar: false
        }
    },
    methods: {
        addTodo(){
            this.data={
                id: this.conter,
                title : this.title,
                description : this.description,
                time : this.time,
                mark : this.mark
            }

            // push in Todos
            this.Todos.push(this.data);
            this.conter++

            // Save Data 
            localStorage.setItem('Todos', JSON.stringify(this.Todos))
            localStorage.setItem('conter', this.conter)

            this.title = "";
            this.description = "";
            this.time = "";
            this.mark = "";

            this.UsSnackbar = true;
        }
    },
}
</script>