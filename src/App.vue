<template>

  <h1>Starting Interview...</h1>
  <GiovanniComponent/>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import GiovanniComponent from "./components/AesticoComponent.vue"


export default defineComponent({
  data(){
          return{

            }
        },

  name: 'App',
  components: {
    GiovanniComponent
  
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #3b90e6;
  margin-top: 60px;
}
html{
    background-color: rgb(226, 226, 226);
}
</style>
