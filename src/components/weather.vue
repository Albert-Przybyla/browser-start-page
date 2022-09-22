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
            <div class="showResults" v-if="showResults" >
                <div class="list" v-for="location in locations" :key="location.lat">{{location.country}}, {{location.name}}</div>
            </div>
        </div>
        <div class="locationBox">
            <div class="location">Poznan, PL</div>
            <div class="date">21 wrzesnia 2022</div>
            <div class="weatherInfo">
            <div class="temp">9°c</div>
            <div class="weather">
                <span class="material-symbols-outlined">
                    weather_snowy
                </span>
                <br>
                rain
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
            weather: {},
            locations: [],
            query: '',
            showResults: false,
        }
    },
    methods: {
        handleInput: debounce(function() {
            if(this.query.length>0){
            axios.get(`${this.api_geo_url}${this.query}&limit=5&appid=${this.api_key}`)
                .then((response) => {
                    this.locations - response.data
                    console.log(response.data)
                    this.showResults = true
                })
                .catch((error) => {
                    console.log(error)
                })
            }else{
                this.showResults = false
            }
        }, 1000)
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
        bottom: 0;
        left: 50;
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