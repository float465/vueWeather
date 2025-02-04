<script>
export default {
	data() {
		return {
			city: ""
		}
	}
}
</script>

<template>
	<div class="wrapper">
		<h1>Погодное приложение</h1>
		<p>Узнать погоду в {{ city == "" ? "вашем городе" : city }}</p>
		<input type="text" v-model="city" placeholder="Введите город">
		<button>Получить погоду</button>
	</div>
</template>

<style scoped>
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
