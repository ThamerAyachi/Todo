<template>
  <v-app>
    <v-main>
        <Navbar/>
        <v-container>
          <v-btn block class="primary my-3" @click="Oform()">{{ Tform }}</v-btn>
          <Form v-if="form"/>
          <Card/>
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
    Tform:"Open Form"
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
};
</script>
