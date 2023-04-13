<template>
  <div class="app">
    <nav class="navbar">
      <img src="assets/logo.png" alt="Game Tracker" style="float: right; height: 100%;">
    </nav>
    <div class="container">
        <div class="content">
          <div class="filters">
            <!-- Filtros aqui -->
          </div>
		<div class="product-list-container">
			<ProductCard v-for="product in products" :key="product.gameID" :product="product" />
		</div>
        </div>
      </div>
    </div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue';

export default {
  components: {
    ProductCard,
  },
  data() {
    return {
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
      ],
    };
  },
};
</script>

<style>
	body {
		background: linear-gradient(45deg, #0B1641 0%, #C70160 100%);
		position: relative;
	}
	nav {
		background-color: #0B1641;
		width: 100%;
		height: 50px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin: 0;
	}
	.product-list-container {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		grid-gap: 20px;
		position: absolute;
		width: 1180px;
		height: 1064px;
		left: 130px;
		top: 246px;
	}
</style>