<template>
	<div class="app">
		<nav class="navbar">
			<img class="logo" :src="require('@/assets/logo/logo.png')" alt="Game Tracker">
		</nav>
		<div class="container">
			<div class="content">
				<h1>Ofertas</h1>
				<div class="filters row">
					<div class="search-filter col-md-6 col-sm-8">
						<input class="search-input" type="text" v-model="searchTerm" placeholder="Procurar"/>
					</div>
					<div class="col-md-6 col-sm-4">
						<label class="order-by-label" >Ordenar por:</label>
						<select class="order-by" id="order-select" v-model="order">
						<option value="discount">% de Desconto</option>
						<option value="price-desc">Maior preço</option>
						<option value="price-asc">Menor preço</option>
						<option value="title">Título</option>
					</select>
					</div>
				</div>
				<div class="product-list-container">
					<div class="text" v-if="searched && filteredProducts.length === 0">Desculpe, não achamos produtos correspondentes a sua pesquisa.</div>
					<div class="product-list">
						<ProductCard v-for="product in orderedProducts" :key="product.gameID" :product="product" />
						<button class="product-see-more">Carregar Mais</button>
					</div>
				</div>
			</div>
		</div>
		<!-- <FooterApp /> -->
	</div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue';
// import FooterApp from '@/components/FooterApp.vue';

export default {
	components: {
		ProductCard,
		// FooterApp,
	},
	data() {
		return {
			order: 'discount',
			searchTerm: '',
			searched: false,
			products:[
				{
					"internalName": "COMPUTERCATS",
					"title": "Computer Cats",
					"metacriticLink": "/game/pc/computer-cats",
					"dealID": "IcPdZfz4Wh1RMK87DOEWsI0ceFyx%2BAlqXB9NiPU52Xw%3D",
					"storeID": "1",
					"gameID": "253951",
					"salePrice": "3.49",
					"normalPrice": "34.99",
					"isOnSale": "1",
					"savings": "90.025722",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "100",
					"steamRatingCount": "10",
					"steamAppID": "2203650",
					"releaseDate": 1669593600,
					"lastChange": 1681092680,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2203650/capsule_sm_120.jpg?t=1674193765"
				},
				{
					"internalName": "SOCIALCREDITSIMULATOR",
					"title": "Social Credit Simulator",
					"metacriticLink": "/game/pc/social-credit-simulator",
					"dealID": "DUzrlG26DMIVIRMqx8JQweUSCcWd6GCAO5%2FcYxw3x0E%3D",
					"storeID": "1",
					"gameID": "253809",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "83",
					"steamRatingCount": "18",
					"steamAppID": "2207070",
					"releaseDate": 1669161600,
					"lastChange": 1681093564,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2207070/capsule_sm_120.jpg?t=1678008486"
				},
				{
					"internalName": "KALZOON",
					"title": "Kalzoon",
					"metacriticLink": "/game/pc/kalzoon",
					"dealID": "W5E6D88P73vmXw6YJZhE%2B1lJQOcwtBEH8aw0DDigwbs%3D",
					"storeID": "1",
					"gameID": "253753",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "100",
					"steamRatingCount": "14",
					"steamAppID": "2206690",
					"releaseDate": 1669075200,
					"lastChange": 1681093148,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2206690/capsule_sm_120.jpg?t=1678345812"
				},
				{
					"internalName": "CRISPYPUPPY",
					"title": "Crispy Puppy",
					"metacriticLink": "/game/pc/crispy-puppy",
					"dealID": "UVwyUCD5oiEUxFHnGbfE9nofN%2BqpayRlR1yCWam0YHg%3D",
					"storeID": "1",
					"gameID": "253752",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "88",
					"steamRatingCount": "17",
					"steamAppID": "2203660",
					"releaseDate": 1669075200,
					"lastChange": 1681092559,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2203660/capsule_sm_120.jpg?t=1674194844"
				},
				{
					"internalName": "STOLENDOLLS",
					"title": "Stolen Dolls",
					"metacriticLink": "/game/pc/stolen-dolls",
					"dealID": "oX36Enf6TeeWebvaLJ9GdoxiCUVR%2BufUD6oTd0yj1vY%3D",
					"storeID": "1",
					"gameID": "253672",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "92",
					"steamRatingCount": "13",
					"steamAppID": "2207080",
					"releaseDate": 1668988800,
					"lastChange": 1681094142,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2207080/capsule_sm_120.jpg?t=1678008523"
				},
				{
					"internalName": "CULTOFTHEMASK",
					"title": "Cult of the Mask",
					"metacriticLink": "/game/pc/cult-of-the-mask",
					"dealID": "QY%2FVUy9XjWvoPnFcBdvMmFUEIeKx4ckLKXuG8vuIre8%3D",
					"storeID": "1",
					"gameID": "253676",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "92",
					"steamRatingCount": "13",
					"steamAppID": "2203680",
					"releaseDate": 1668988800,
					"lastChange": 1681091520,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2203680/capsule_sm_120.jpg?t=1674194851"
				},
				{
					"internalName": "ANTSOFDUTY",
					"title": "Ants of Duty",
					"metacriticLink": "/game/pc/ants-of-duty",
					"dealID": "IV1aG61bHAyKAIhO%2FmMccpXWUUKPH%2BmZ5hr1Y1RGtfw%3D",
					"storeID": "1",
					"gameID": "253675",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "87",
					"steamRatingCount": "16",
					"steamAppID": "2203610",
					"releaseDate": 1668988800,
					"lastChange": 1681092961,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2203610/capsule_sm_120.jpg?t=1669738693"
				},
				{
					"internalName": "FURRYKILLER",
					"title": "Furry Killer",
					"metacriticLink": "/game/pc/furry-killer",
					"dealID": "SyD8mSYLSjTRW60JSu1CIuBxIR4zwOvvAPuDs4HO4X0%3D",
					"storeID": "1",
					"gameID": "253648",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Mostly Positive",
					"steamRatingPercent": "77",
					"steamRatingCount": "22",
					"steamAppID": "2206460",
					"releaseDate": 1668816000,
					"lastChange": 1681092667,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2206460/capsule_sm_120.jpg?t=1678264634"
				},
				{
					"internalName": "KINGSMASH",
					"title": "King Smash",
					"metacriticLink": "/game/pc/king-smash",
					"dealID": "kO%2FGrOrftoJ04yAAJz1%2BVgFuQ7lt5ZD72zYgm5yaU%2Fg%3D",
					"storeID": "1",
					"gameID": "253640",
					"salePrice": "2.99",
					"normalPrice": "29.99",
					"isOnSale": "1",
					"savings": "90.030010",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "92",
					"steamRatingCount": "13",
					"steamAppID": "2206700",
					"releaseDate": 1668816000,
					"lastChange": 1681093334,
					"dealRating": "9.2",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2206700/capsule_sm_120.jpg?t=1678345820"
				},
				{
					"internalName": "BREATHSPACE",
					"title": "Breathspace",
					"metacriticLink": "/game/pc/breathspace",
					"dealID": "wjntXSvtD5u8XBqXgdSaDovm80YyVh9IclO3LrdKFqE%3D",
					"storeID": "1",
					"gameID": "253681",
					"salePrice": "3.49",
					"normalPrice": "34.99",
					"isOnSale": "1",
					"savings": "90.025722",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "93",
					"steamRatingCount": "15",
					"steamAppID": "2203640",
					"releaseDate": 1668988800,
					"lastChange": 1681094193,
					"dealRating": "9.1",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2203640/capsule_sm_120.jpg?t=1669738708"
				},
				{
					"internalName": "POWERDRIVER",
					"title": "Power Driver",
					"metacriticLink": "/game/pc/power-driver",
					"dealID": "0wKwJJ6DNHfDQG2aum7Ga%2BsQ2G%2Bx6A1CE92h3%2Bb9i9o%3D",
					"storeID": "1",
					"gameID": "253671",
					"salePrice": "3.49",
					"normalPrice": "34.99",
					"isOnSale": "1",
					"savings": "90.025722",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "92",
					"steamRatingCount": "14",
					"steamAppID": "2207110",
					"releaseDate": 1668988800,
					"lastChange": 1681093855,
					"dealRating": "9.1",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2207110/capsule_sm_120.jpg?t=1678008375"
				},
				{
					"internalName": "LABINSPECT",
					"title": "Lab Inspect",
					"metacriticLink": "/game/pc/lab-inspect",
					"dealID": "YLq6yiiBu5bDwgZ0KUdMzdf64KLBTjSkYg5U%2FG44Y3I%3D",
					"storeID": "1",
					"gameID": "253689",
					"salePrice": "3.49",
					"normalPrice": "34.99",
					"isOnSale": "1",
					"savings": "90.025722",
					"metacriticScore": "0",
					"steamRatingText": "Positive",
					"steamRatingPercent": "93",
					"steamRatingCount": "15",
					"steamAppID": "2206720",
					"releaseDate": 1668988800,
					"lastChange": 1681093325,
					"dealRating": "9.1",
					"thumb": "https://cdn.cloudflare.steamstatic.com/steam/apps/2206720/capsule_sm_120.jpg?t=1678345829"
				}
			]
		};
	},
	computed: {
		filteredProducts() {
			if (this.searchTerm !== '') {
				return this.products.filter(product => {
					return product.title.toLowerCase().includes(this.searchTerm.toLowerCase());
				});
			} else {
				return this.products;
			}
		},

		orderedProducts() {
			let filteredProducts = [...this.products]; // cria uma cópia do array original
			filteredProducts = this.filterProducts(filteredProducts); // aplica o filtro
			filteredProducts = this.sortProducts(filteredProducts); // aplica a ordenação
			if (this.searched && !this.products.length) {
				return [];
			} else if (this.searchTerm) {
				return this.products.filter(product => product.title.toLowerCase().includes(this.searchTerm.toLowerCase()));
			} else {
				return filteredProducts;
			}
		},
	},
	methods: {
		searchProducts() {
			this.searched = true;
            this.$emit('search', this.searchTerm);
        },

		filterProducts(products) {
			return products.filter((product) =>
				product.title.toLowerCase().includes(this.searchTerm.toLowerCase())
			);
		},
		
		sortProducts(products) {
			switch (this.order) {
			case "discount":
				return products.sort((a, b) => a.savings - b.savings);
			case "price-asc":
				return products.sort((a, b) => a.salePrice - b.salePrice);
			case "price-desc":
				return products.sort((a, b) => b.salePrice - a.salePrice);
			default:
				return products.sort((a, b) => a.title.localeCompare(b.title));
			}
		},
	},
	watch: {
		searchTerm() {
			if (this.searchTerm !== '') {
				this.searched = true;
			} else {
				this.searched = false;
			}
		}
	}
};
</script>

<style>
	@import "@/components/css/Home.css";
</style>
