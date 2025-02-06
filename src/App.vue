<script>
import axios from 'axios'

export default {
	data() {
		return {
			city: "",
			error: "",
			info: null
		}
	},
	computed: {
		cityName() {
			return this.city
		},
		showTemp() {
			return "Температура: " + this.info.main.temp
		},
		showFeelsLike() {
			return "Ощущается как: " + this.info.main.feels_like
		},
		showMinTemp() {
			return "Минимальная температура: " + this.info.main.temp_min
		},
		showMaxTemp() {
			return "Максимальная температура: " + this.info.main.temp_max
		},

	},
	methods: {
		getWeather() {
			if(this.city.trim().length < 2) {
				this.error = "Нужно название более одного символа :)"
				return false
			}

			this.error = ""

			axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=64007cb8a701ec79f75917dcb4d3c76e`)
				.then(res => (this.info = res.data))

		}
	}
}
</script>

<template>
	<div class="wrapper">
		<h1>Погодное приложение</h1>
		<p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
		<input type="text" v-model="city" placeholder="Введите город">
		<button v-show="city != ''" @click = "getWeather()">Получить погоду</button>
		<p class="error">{{ error }}</p>

		<div class="a" v-if="info != null">
			<p>{{ info.main.temp }}</p>
			<p>{{ showTemp }}</p>
			<p>{{ showFeelsLike }}</p>
			<p>{{ showMinTemp }}</p>
			<p>{{ showMaxTemp }}</p>
		</div>
	</div>
</template>

<style scoped>



.error{
	color: rgb(223, 141, 145);
	font-size: 13px;
}
	.wrapper{
		width: 900px;
		height: 500px;
		border-radius: 50px;
		padding: 20px;
		background: rgb(2,0,36);
		background: linear-gradient(160deg, rgba(2,0,36,1) 0%, rgba(53,207,240,1) 0%, rgba(0,212,255,1) 7%, rgba(255,255,255,1) 100%);
		text-align: center;
		color: white;
	}
	.wrapper h1{
		margin-top: 50px;
	}
	.wrapper p{
		margin-top: 20px;
	}
	
	.wrapper input{
		margin-top: 30px;
		background: transparent;
		border: 0;
		border: 2px solid #cacaca;
		color: #fcfcfc;
		font-size: 14px;
		padding: 5px 8px;
		outline: none;
	}
	
	.wrapper button{
		background: linear-gradient(90deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
		background-size: 400% 400%;
		animation: gradient 10s ease infinite;
		transform: translate3d(0, 0, 0);
		border: 0;
		height: 29px;
		width: 150px;
		cursor: pointer;
	}

	@keyframes gradient {
				0% {
		background-position: 0% 50%;
	}
	50% {
		background-position: 100% 50%;
	}
	100% {
		background-position: 0% 50%;
	}
	}

</style>
