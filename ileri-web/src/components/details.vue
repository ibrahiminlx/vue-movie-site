<template>
	<div class="details">
		<h2>{{ proId }}</h2>
		<h2>{{ data }}</h2>
		<div class="container">
			<div class="row">
				<div class="col-md-12" v-for="(product, index) in products" :key="index">
					<div v-if="proId == product.productId">
						<h1>{{ product.productTitle }}</h1>
						<img :src="product.image" class="img-fluid">
						<p></p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
import axios from "axios";
import home from "./home";







export default {
	name: 'details',
	data() {
		return {
			proId: this.$route.params.Pid,
			detailss: {
				method: 'GET',
				url: 'https://flixster.p.rapidapi.com/movies/detail',
				params: { emsVersionId: this.$route.params.Pid, },
				headers: {
					'X-RapidAPI-Key': '29e5c17275mshc405a3ab6085034p10d53djsn0266442dc3d9',
					'X-RapidAPI-Host': 'flixster.p.rapidapi.com'
				}
			},
			title: "details",
			products: [
				{
					productTitle: "ABCN",
					image: require('../assets/images/product1.png'),
					productId: 1
				},
				{
					productTitle: "KARMA",
					image: require('../assets/images/product2.png'),
					productId: 2
				}
			], data: [],


		}

	}
	,
	created() {
		console.log(this.detailss);
	}
	,
	mounted() {
		console.log(this.detailss);
		  axios
			.request(this.detailss)
			.then(response => (this.data = response.data.data.movie.name))

	},



}

</script>
