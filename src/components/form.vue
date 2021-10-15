<template>
    <v-card class="my-3">
        <v-container>
            <v-form class="form">
                <h2 class="secondary--text">Add new Todo :</h2>
                <v-text-field label="Title" v-model="title"></v-text-field>
                <v-textarea label="Description" v-model="description"></v-textarea>
                <v-time-picker format="ampm" full-width v-model="time"></v-time-picker>
                <v-select :items="items" label="Mark" v-model="mark"></v-select>
                <v-btn block color="primary" class="mt-6" @click="showData()">Add Todo</v-btn>
            </v-form>
        </v-container>
    </v-card>
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
            items:["M-Blue", "M-Red", "M-Green", "M-Yallow"]
        }
    },
    methods: {
        showData(){
            this.data={
                title : this.title,
                description : this.description,
                time : this.time,
                mark : this.mark
            }
            console.log(`
            Title: ${this.data.title}
            Description: ${this.data.description}
            Time: ${this.data.time}
            Mark: ${this.data.mark}
            `)
        }
    },
}
</script>