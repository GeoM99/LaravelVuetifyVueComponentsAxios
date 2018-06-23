<template>
   
    <v-app>


    <v-toolbar>
    <v-toolbar-title>List Users With Laravel Vuetify VueComponents Axios</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      
    </v-toolbar-items>
  </v-toolbar>


<v-container>
     <v-data-table
    :headers="headers"
    :items="users"
    hide-actions
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td></td>
      <td class="text-xs-left">{{props.item.id}}</td>
      <td class="text-xs-left">{{props.item.name}}</td>
      <td class="text-xs-left">{{props.item.email}}</td>
      <td class="text-xs-left">{{props.item.phone}}</td>
      <td class="text-xs-left">{{props.item.username}}</td>
    </template>
  </v-data-table>
  </v-container>

    </v-app>

</template>

<script>
    import axios from 'axios';

    export default {
        data(){
            return {
               users : [],
            
            headers: [
          {
            align: 'center',
            sortable: false,
            value: 'name'
          },
          { text: 'Id', value: 'id' },
          { text: 'Name', value: 'name' },
          { text: 'Email', value: 'email' },
          { text: 'Phone', value: 'phone' },
          { text: 'UserName', value: 'username' }
        ],
      }


           
        },

        methods:{
            getData(){
                axios.get('https://jsonplaceholder.typicode.com/users')
                .then(response =>{
                    console.log(response.data)
                    this.users = response.data
                })
                .catch(e=>{
                    console.log(e)
                })
            }

        },

        mounted(){
            this.getData()
        }
    }
</script>
