<template>
  <div class="card-container">
    <div class="card">
      <div class="card-image">
        <img :src="product.thumb" alt="">
      </div>
      <div class="card-content" :style="{ backgroundColor: '#0B1641' }">
        <div class="card-title">{{ product.title }}</div>
        <div class="card-price">
          <div class="card-price-current">{{ product.salePrice }}</div>
          <div class="card-price-original">{{ product.normalPrice }}</div>
          <div class="card-discount">{{ getDiscountText(product) }}</div>
        </div>
        <div class="card-details" :style="{ backgroundColor: '#C70160' }">
          <button>Detalhes</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
	props: {
		product: {
		type: Object,
		required: true,
		},
	},
	methods: {
		getDiscountText(product) {
			if (product.isOnSale) {
				const savings = parseFloat(product.savings);
				if (!isNaN(savings)) {
					if (savings === 100) {
						return 'Grátis';
					} else {
						return `-${savings.toFixed(0)}%`;
					}
					} else {
					return '';
					}
				} else {
					return '';
			}
		}
	}
};
</script>

<style scoped>
	.card-container {
		display: flex;
		flex-wrap: wrap;
		margin: 0 auto;
	}

	.card {
		display: flex;
		flex-direction: column;
		margin-bottom: 10px;
	}
	.card-image img {
		width: 380px;
		height: 147px;
		object-fit: cover;
	}

	.card-content {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 10px;
	}

	.card-title {
		font-size: 1.2rem;
		font-weight: bold;
		text-align: left;
		color: white;
		font-family: 'Roboto';
	}

	.card-price {
		font-size: 1.2rem;
		font-weight: bold;
		text-align: center;
		color: white;
		font-family: 'Roboto';
	}

	.card-price-original {
		font-size: 0.8rem;
		text-align: center;
		color: white;
		text-decoration: line-through;
		margin-top: 5px;
		font-family: 'Roboto';
	}

	.card-discount {
		font-size: 0.8rem;
		text-align: right;
		color: white;
		font-family: 'Roboto';
	}

	.card-details {
		text-align: center;
		padding: 10px;
	}

	button {
		background-color: #C70160;
		color: white;
		font-weight: bold;
		border: none;
		padding: 5px 10px;
		cursor: pointer;
		font-family: 'Roboto';
	}
</style>