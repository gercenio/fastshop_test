<template>
    <div>
        <label>Anos</label>
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
                "name":"2019"
            },
            {
                "name":"2018"
            },
            {
                "name":"2017"
            },
            {
                "name":"2016"
            }],
            object: {
              name: 'Anos',
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