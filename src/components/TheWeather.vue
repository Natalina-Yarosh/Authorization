<template>
   <div>
        <TheLoader v-if="isLoading"/>
        <div v-else class="item">
            <CityImage :cityImage="cityImage" :className="className"   :temperature="temperature" :city="city"/>
            <WeatherInfo
            :city="city"
            :temperature="temperature"
            :info="info"
            :temperatureMin="temperatureMin"
            :temperatureMax="temperatureMax"
            :currentDate="currentDate"
            :icon="icon"
            />
        </div>
        <div class="pokemon-list">
            <h1>Pokemon list</h1>
            <ul>
                <li v-for="(result, index) in resultsName" :key="index" @click="showPokemonInfo(result.url)">
                    <p>{{ result.name }}</p>
                </li>
            </ul>
        </div>
        <div v-if="selectedPokemon">
            <h2>{{ selectedPokemon.name }}</h2>
           
            <!-- Добавьте другие поля информации о покемоне по вашему усмотрению -->
        </div>
        <div v-for="(resulttest, index) in selectedPokemonAbilities" :key="index" @click="showPokemonInfoTest(resulttest.ability.url)">
            <h2>{{ resulttest.ability.name }}</h2>
        </div>
        <div v-for="(resulttest1, index) in selectedPokemonAbilitiesEffect" :key="index" >
            <h2>{{ resulttest1.effect}}</h2>
        </div>

   </div>
</template>

<script>
import dayjs from 'dayjs';
import axios from 'axios';
import { openWeatherMapApiUrl, openImageApiUrl, openElemApiUrl } from '../api.js';

import CityImage from './CityImage.vue';
import WeatherInfo from './WeatherInfo.vue';
import TheLoader from './TheLoader.vue';

export default {
    components: {
        CityImage,
        WeatherInfo,
        // TheLoader
    },
    data(){
      return{
        temperature: '',
        temperatureMin: '',
        temperatureMax: '',
        city: '',
        date:'',
        info:'',
        degrees: '',
        currentDate: dayjs().locale('en').format('dddd, D MMMM'),
        className:'',
        icon:'',
        cityImage: '',
        isLoading: true,
        resultsName: [],
        selectedPokemon: null,
        selectedPokemonAbilities: [],
        selectedPokemonAbilitiesEffect: [],
      }
    },
    mounted(){
        this.getLocation();
       
    },
    methods:{
        // getLocation() {
        //     if (navigator.geolocation) {
        //         navigator.geolocation.getCurrentPosition((position) => {
        //             // this.showWeather(position); 
        //             // this.fetchRandomCityImage();
        //             this.fetchRandomCityElem()
        //         });
        //     } else {
        //         alert("Geolocation is not supported by your browser.");
        //     }
        // },
        // async showWeather(position) {
        //     const apiKey = '3d51f680ac485452eada2b919d5a39bd';
        //     const latitude = position.coords.latitude;
        //     const longitude = position.coords.longitude;
        //     const weatherApiUrl = `${openWeatherMapApiUrl}?lat=${latitude}&lon=${longitude}&appid=${apiKey}`;


        //     axios
        //         .get(weatherApiUrl)
        //         .then(response => {
        //             this.isLoading = false;
        //             const data = response.data;
        //             this.city = data.name;
        //             this.temperature = (data.main.temp - 273.15).toFixed(1);
        //             this.info = data.weather[0].description;
        //             this.temperatureMin = (data.main.temp_min - 273.15).toFixed(1);
        //             this.temperatureMax = (data.main.temp_max - 273.15).toFixed(1);
        //             const iconCode = data.weather[0].icon;
        //             this.icon = `https://openweathermap.org/img/wn/${iconCode}.png`;

        //             if (this.temperature < -10) {
        //                 this.className = 'blue';
        //             } else if (this.temperature > -10 && this.temperature <= 10) {
        //                 this.className = 'light-blue';
        //             } else if (this.temperature > 10 && this.temperature <= 25) {
        //                 this.className = 'yellow';
        //             } else {
        //                 this.className = 'red';
        //             }
        //         })
        //         .catch(error => console.error('Error during API request:', error));
        // },
        // async fetchRandomCityImage() {
        //     const imageApiUrl = `${openImageApiUrl}`;
        //     try {
        //         const response = await axios.get(imageApiUrl, {
        //             params: {
        //                 query: 'city',
        //                 orientation: 'landscape',
        //                 client_id: 'ofMQDoT-icgdK_vQb4PitqCNYTa5KL-msxb5BrnHjr8',
        //             },
        //         });
        //         this.cityImage = response.data.urls.regular;
        //     } catch (error) {
        //         console.error('Error when uploading an image:', error);
        //     }
        // },
        async fetchRandomCityElem() {
            const elemApiUrl = `${openElemApiUrl}`;
            axios
                .get(elemApiUrl)
                .then(response => {
                    const data = response.data;
                    // console.log('data', data.results);
                    this.resultsName = data.results;
                    // console.log('data 1', this.resultsName);
                })
                .catch(error => console.error('Error during API request:', error));
        },
        async showPokemonInfo(url) {
            try {
                this.selectedPokemon = null;
                this.selectedPokemonAbilities =  [];
                this.selectedPokemonAbilitiesEffect= [];
                const response = await axios.get(url);
                console.log('response.data', response.data);
                this.selectedPokemon = response.data.forms[0];
                this.selectedPokemonAbilities = response.data.abilities;
                console.log('this.selectedPokemonAbilities', this.selectedPokemonAbilities);
               
            } catch (error) {
                console.error('Error getting Pokemon info:', error);
            }
        },
        async showPokemonInfoTest(url) {
            try {
                const response = await axios.get(url);
                console.log('response.data', response.data.effect_entries);
                this.selectedPokemonAbilitiesEffect = response.data.effect_entries;
            } catch (error) {
                console.error('Error getting Pokemon info:', error);
            }
        }
    },
    mounted() {
    // Вызовите метод после монтирования компонента или в другом удобном месте
    this.fetchRandomCityElem();
  }
}
</script>

<style scoped>
.item {
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0px 9px 19px 0px #121620;
    min-width: 300px;
}
</style>