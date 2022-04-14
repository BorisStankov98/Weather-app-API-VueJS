<script setup>
import NewCity from './components/NewCity.vue';
</script>

<template>
<div>
  <div id="head">
  <h1>Data for the bigger cities is preloaded</h1>
  <h3> you can also add some of your own via the form below:</h3>
  </div>
 
 <NewCity/>
</div>
</template>


<script>
export default{
  name:"app",
  components:{
  NewCity,
  },
  data(){
    return{
     
    }
  },
  methods:{
    
  }
}
</script>
<style>
@import './assets/base.css';
</style>
