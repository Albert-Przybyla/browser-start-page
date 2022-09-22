<script setup>
    import debounce from 'https://unpkg.com/vue-debounce@3.0.2/dist/debounce.min.mjs';
    import axios from 'axios';
</script>

<template>
    <div class="weatherBox">
        <div class="search">
            <input type="text" 
            name="" 
            id=""
            placeholder="search location ..."
            v-model="query"
            @input="handleInput"
            >
        </div>
        <div class="showResults" v-if="showResults" >
            <div class="list" @click="showWeather(location.lat, location.lon)" v-for="location in locations" :key="location.name">{{location.name}}, {{location.country}}, {{location.state}}</div>
        </div>
        <div class="locationBox" v-if="showWeatherInfo">
            <div class="location">{{weather.data.name}}, {{weather.data.sys.country}}</div>
            <div class="date">{{date.getDate()}}.{{date.getMonth()}}.{{date.getFullYear()}}</div>
            <div class="weatherInfo">
            <div class="temp">{{Math.round(weather.data.main.temp)}}°c</div>
            <div class="weather">
                <span class="material-symbols-outlined">
                    weather_snowy
                </span>
                <br>
                {{weather.data.weather[0].main}}
            </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "weather",
    components: {

    },
    data() {
        return {
            api_key: '0a3bb1ff2db0e040a9982a1d81f55253',
            api_geo_url: 'http://api.openweathermap.org/geo/1.0/direct?q=',
            api_url: 'https://api.openweathermap.org/data/2.5/weather?',
            weather: {},
            locations: [],
            query: '',
            showResults: false,
            showWeatherInfo: false,
            date: '',
        }
    },
    methods: {
        handleInput: debounce(function() {
            if(this.query.length>0){
            axios.get(`${this.api_geo_url}${this.query}&limit=5&appid=${this.api_key}`)
                .then((response) => {
                    this.locations = response.data
                    console.log(response.data)
                    this.showResults = true
                })
                .catch((error) => {
                    console.log(error)
                })
            }else{
                this.showResults = false
            }
        }, 1000),

        showWeather(lat, lon){
            this.showResults = false
            console.log(lat)
            axios.get(`${this.api_url}lat=${lat}&lon=${lon}&units=metric&appid=${this.api_key}`)
                .then((response) => {
                    console.log(response)
                    this.weather = response
                    this.showWeatherInfo = true
                })
                .catch((error) => {
                    console.log(error)
                })
        },   
        curentUserLocation() { 
            navigator.geolocation.getCurrentPosition( 
                position => {  
                this.showWeather(position.coords.latitude, position.coords.longitude)
            })
        },
        dataBuilder() {
            this.date = new Date() 
        }
    },
    beforeMount(){
        this.curentUserLocation(),
        this.dataBuilder()
    }


    }
</script>

<style scoped>
    .weatherBox{
        width: 90%;
        height: 65vh;
        border-radius: 20px;
        background-image: url(../assets/cold-bg.jpeg);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;
        transition: .4s;
        display: flex;
        flex-direction: column;
    }

    .search{
        width: 100%;
        height: 15vh;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    input{
        width: 250px;
        height: 40px;
        font-size: 20px;
        background-color: #181818;
        color: rgba(235, 235, 235, 0.64);
        text-align: center;
        border-radius: 15px;
        border: none;
    }

    input:focus{
        outline: none;
    }

    .showResults {
        color: rgba(235, 235, 235, 0.64);
        background-color: #181818;
        position: absolute;
        top: 20%;
        left: 20%;
        right: 20%;
        z-index: 2;
        border-radius: 15px;
        text-align: center;
        padding: 10px;
    }

    .list:hover{
        cursor: pointer;
        background-color: #292929;
    }

    .locationBox{
        color: black;
        display: flex;
        flex-direction: column;
        height: 50vh;
        align-items: center;
        justify-content: flex-start;
    }

    .weatherInfo{
        margin-top: 20px;
        padding: 20px;
        background-color: rgba(255,255,255, 0.50);
        border-radius: 15px;
        box-shadow: 3px 6px rgba(54, 54, 54, 0.787);
    }

    .location{
        font-size: 28px;
    }
    .temp{
        font-size: 50px;
        margin: 20px;
    }

    .weather{
        font-size: 30px;
        text-align: center;
    }

    .weather span{
        font-size: 40px;
        text-align: center;
    }
</style>