<template>
	<div class="informer-container">
		<Temperature :real="weather.temp_real" :feel="weather.temp_feel"></Temperature>
		<FlexBreak></FlexBreak>

		<Humidity :val="weather.humidity"></Humidity>
		<VerticalDivider></VerticalDivider>
		<Wind :val="weather.wind"></Wind>
	</div>
</template>

<script>
import Temperature from "./Temperature.vue";
import Humidity from "./Humidity.vue";
import Wind from "./Wind.vue";
import FlexBreak from "./FlexBreak.vue";
import VerticalDivider from "./VerticalDivider.vue";

export default {
	name: "Container",
	props: ['weather'],
	components: {
		Temperature,
		Humidity,
		Wind,
		FlexBreak,
		VerticalDivider,
	}
};
</script>

<style>
.informer-container {
	display: flex;
	align-items: flex-start;
	justify-content: space-between;
	flex-wrap: wrap;
	width: 400px;
	padding: 30px;
	background-image: url("/img/forest.png");
	background-size: cover;
	background-position: center center;
	border-radius: 20px;
	box-shadow: 0px 0px 10px 0px rgba(50, 50, 50, 0.75);
}
</style>
