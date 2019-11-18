<template>
  <div id="app">
   <FormComponent @isshow="isshow"></FormComponent>
    <HelloWorld v-if="isshowvar" msg="Welcome to Your Vue.js App"/>
   
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import FormComponent from './components/formcomponent.vue'

export default {
  name: 'app',
      data(){
          return {
             isshowvar:false,
           };
        },

  components: {
    HelloWorld,
    FormComponent
  },
  methods:{
    
            isshow(isshow) {
             
                this.isshowvar = isshow;
                
            }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
