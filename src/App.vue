<template>
	<div id="app">
		<Container :weather="weather"></Container>
	</div>
</template>

<script>
import Container from "./components/Container.vue";

export default {
	name: "App",
	components: {
		Container,
	},
	data() {
		return {
			weather: {
				temp_real: 0,
				temp_feel: -3.5,
				humidity: 5,
				wind: 20,
			},
			timerId: ""
		};
	},
	methods: {
		getTemp() {
			this.axios
				.get("http://37.77.104.246/api/weather/temp.php")
				.then((response) => {
					this.weather.temp_real = response.data;
				});
		},

		getFeel() {
			this.axios
				.get("http://37.77.104.246/api/weather/feel.php")
				.then((response) => {
					this.weather.temp_feel = response.data;
				});
		},

		getWind() {
			this.axios
				.get("http://37.77.104.246/api/weather/wind.php")
				.then((response) => {
					this.weather.wind = response.data;
				});
		},

		getHumidity() {
			this.axios
				.get("http://37.77.104.246/api/weather/humidity.php")
				.then((response) => {
					this.weather.humidity = response.data;
				});
		},

		getWeather() {
			console.log(123);
			this.getTemp();
			this.getFeel();
			this.getWind();
			this.getHumidity();
		}
	},
	mounted() {
		this.getWeather();

		const self = this;
		this.timerId = setInterval(function() {
			self.getWeather();
		}, 5000);
	},
};
</script>

<style>
body {
	margin: 0;
	padding: 0;
}

#app {
	display: flex;
	align-items: center;
	justify-content: center;
	height: 100vh;
	background: rgb(244, 123, 186);
	background: linear-gradient(
		-25deg,
		rgba(244, 123, 186, 0.5) 20%,
		rgba(90, 95, 245, 0.5) 80%
	);
}
</style>
