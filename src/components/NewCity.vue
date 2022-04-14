<template>
<div>
 <form class="form" @submit.prevent="onSubmit" @submit="addCity" >
    <input  id="input" type="text" placeholder="Type a city" v-model="myText">
    <button id="button">Submit</button>
  </form>
        <City :array = "dataArray"/>
    </div>
</template>

<script>
import axios from 'axios'
import City from './City.vue'

export default{
    name: "form",
     mounted() {
       this.callApi()
    },
    data() {
        return {
            innitialArray:["sofia","varna","burgas","plovdiv",],
            apiKey: "a6f922dcdd663a60627025e5586baeff",
            dataArray: []
        };
    },
    props: {
        city: String,
    },
    methods: {
        //on page load renders all pre-decided items
       async callApi(place){
       this.innitialArray.slice(place).forEach((element) => {
       axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${element}&appid=${this.apiKey}&units=metric`)
            .then(res => {
            this.dataArray.push(res.data)
        }).catch(e =>{
          alert(`${this.myText}is not in the database please try another one :)`)
        })   
        })},
        //adds new item and passes the end of the array as the argument for the forEach
      addCity(){
      this.innitialArray.push(this.myText)
      this.callApi(this.innitialArray.length-1)
      // still trying to figure out how to resset the input value this.Mytext = '' resets only the backend value
       }
    },
    components: { City }
}
</script>
