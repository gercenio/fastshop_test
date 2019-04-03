<template>
    <div>
        <label>Generos</label>
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
            arrayOfObjects: [],
            object: {
              name: 'Genres',
            }
          }
        },
    computed: {
            request(){
                return 'https://api.themoviedb.org/3/genre/movie/list?api_key='+storage.apiKey+'&language=en-US';
            }
        },
    components: {
            'dropdown': dropdown,
    },
        methods: {
          methodToRunOnSelect(payload) {
            this.object = payload;
          },
          fetchGenres(){
                axios.get(this.request)
                .then(function(resp){
                this.arrayOfObjects = resp.data.genres;

            }.bind(this))
            .catch(function(error) {
                this.$router.push({ name: '404' });
                }.bind(this));
            }
        },
        created(){
            this.fetchGenres();
        }
      }
</script>