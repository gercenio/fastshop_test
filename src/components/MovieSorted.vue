<template>
    <div>
        <label>Ordenado por</label>
        <dropdown :options="arrayOfObjects" :selected="object" v-on:updateOption="methodToRunOnSelect"></dropdown>
    </div>
</template>

<script>
import dropdown from 'vue-dropdowns'
import storage from '../storage.js'
import axios from 'axios'

export default {
     
     data() {
          return {
            arrayOfObjects: [{
                "name":"Desc"
            },
            {
                "name":"Asc"
            }],
            object: {
              name: 'Ordenação',
            }
          }
        },
    computed: {
           
        },
    components: {
            'dropdown': dropdown,
    },
        methods: {
          methodToRunOnSelect(payload) {
            this.object = payload;
          }
        },          
        created(){
            
        }
      }
</script>