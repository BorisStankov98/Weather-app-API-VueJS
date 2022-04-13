<template>
    <div class="city">
        <div>
        <h1>{{dataArray?.name}}</h1>
        <h2>{{dataArray?.main.temp.toFixed(1)}} &#8451;</h2>
        </div>
        <img style="height:70px" :src='(` http://openweathermap.org/img/wn/${dataArray?.weather[0].icon}.png`)' alt="">
    </div>
</template>

<script>
import axios from 'axios'

export default{
    name:'form',
   async mounted(){
      await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${this.apiKey}&units=metric`)
       .then(res =>{
          
           this.dataArray = res.data
           console.log(this.dataArray)
       })
    },
data(){
    return{
    apiKey : "a6f922dcdd663a60627025e5586baeff",
    dataArray:null,
    }
},
props:{
    city:String,
   
},
methods:{
}
}
</script>

