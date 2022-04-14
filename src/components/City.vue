<template>
     <div className="city">
        <div className="each-city" :key="index" v-for="(city, index) in array">
            <h1>{{city.name}}</h1>
            <h1>{{city.main.temp.toFixed(1)}} &#8451;</h1>
        <img style="height:70px" :src='(`http://openweathermap.org/img/wn/${city.weather[0].icon}.png`)' :alt="city.name">
        </div>
    </div>
</template>
<script>
export default{
    name:'City',
    data(){
        return{
        }
    },
    props:{
        array:Array,
        
    }
}

</script>