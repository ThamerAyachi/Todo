<template>
  <v-app>
    <v-main>
        <Navbar/>
        <v-container>
          <v-btn block class="primary my-3" @click="Oform()">{{ Tform }}</v-btn>
          <Form v-if="form"/>
          <Card v-for="Todo in Todos" :key="Todo.id"
          :title="Todo.title"
          :description="Todo.description"
          :time="Todo.time"
          :mark="Todo.mark"
          :id="Todo.id"
          />
        </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Navbar from "@/components/Navbar";
import Form from "@/components/form";
import Card from "@/components/Card";

export default {
  name: 'App',

  components: {
    Navbar,
    Form,
    Card
  },

  data: () => ({
    form:false,
    Tform:"Open Form",
    Todos: JSON.parse(localStorage.getItem("Todos"))
  }),

  methods: {
    Oform(){
      if(this.form){
        this.Tform = "Open Form"
      }
      else{
        this.Tform = "Close Forme"
      }
      this.form = !this.form
    }
  },
  created() {
    
    // Add default data in local storage
    if (this.Todos == null){
      localStorage.setItem("Todos", JSON.stringify([]))
      localStorage.setItem("conter", 1)
    }

     document.body.addEventListener('click', () => {
       this.Todos = JSON.parse(localStorage.getItem("Todos"))
     })
  },
};
</script>
