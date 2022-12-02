<template>
    <v-row justify="center">
      <v-dialog v-model="dialog" max-width="600px">
        
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" dark v-bind="attrs" v-on="on">Add Person</v-btn>
        </template>

        <v-card>
          <v-card-title><span class="text-h5">User Profile</span></v-card-title>
          
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12" md="4"> <v-text-field v-model="id" label="Enter Unique ID"></v-text-field></v-col>
                <v-col cols="12" md="4"> <v-text-field v-model="name" label="Enter First Name"></v-text-field></v-col>
                <v-col cols="12" md="4"> <v-text-field v-model="email" label="Enter Email"></v-text-field></v-col>
                <v-col cols="12" md="12"> <v-text-field v-model="gender" label="Enter Gender"></v-text-field></v-col>
              </v-row>
            </v-container>
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false">Close</v-btn>
            <v-btn color="blue darken-1" text @click="addPerson()">Save</v-btn>
          </v-card-actions>

        </v-card>
      </v-dialog>
    </v-row>
  </template>

<script>
export default {
  data: () => ({
    dialog: false,
    id: null,
    name: '',
    email: '',
    gender: ''

  }),
  methods:{
    addPerson(){
        
        this.$emit('newPerson', {
            id: this.id,
            first_name: this.name,
            email: this.email,
            gender: this.gender
        })

        this.dialog = false
    }
  }
}
</script>