<script setup>
import NewCity from './components/NewCity.vue';
</script>

<template>
<div>
  <div id="head">
  <h1>Data for the bigger cities is preloaded</h1>
  <h3> you can also add some of your own via the form below:</h3>
  </div>
  <form class="form" @submit.prevent="onSubmit" @submit="addCity">
    <input id="input" type="text" v-model="myText" placeholder="Type a city">
    <button id="button"  >Submit</button>
  </form>
 <NewCity :key="index" v-for="(city, index) in this.cityArray" :city="city"/>
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
      cityArray:["sofia","varna","burgas","plovdiv"]
    }
  },
  methods:{
    addCity(){
      this.cityArray.push(this.myText)
      this.myText = ''
    }
  }
}
</script>
<style>
@import './assets/base.css';
</style>
