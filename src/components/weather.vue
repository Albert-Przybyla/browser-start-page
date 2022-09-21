<script setup>
    import search from "@/components/Search.vue"
</script>

<template>
    <div class="weatherBox">
        <search/>
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
    search
    },
    data() {
        return {
            api_key: 'ccab95902b2f19062b1ea7d4d2ca6c56',
            api_url: 'https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid='
        }
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