<template>

  <div id="app">
    <todo-app></todo-app> 
  <div class="inline-footer">
  
  </div>
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue'

export default {
  name: 'App',
  components: {
    TodoApp
  },


  data(){
    return {
      tasks:[
        {
        name: "Todo Task Name One",
        status: "To-Do"
        },   
        {
        name: "Todo Task Name One",
        status: "To-Do"
        }
      ]
    }
  }


};
</script>

<style>

/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/


todo-app{
  background: #000000ea;
}
*,*::before,*::after{
  margin:0;
  padding:0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #000000c9;
}
</style>
