<template>
  <div class="card-container">
    <div class="card">
      <div class="card-image">
        <img :src="product.thumb" alt="">
      </div>
      <div class="card-content">
        <div class="card-title">{{ product.title }}</div>
        <div class="card-price">
			<div class="card-price-current">{{ product.salePrice }}</div>
			<div class="card-price-original">{{ product.normalPrice }}</div>
			<div class="card-discount"><button class="discount">{{ getDiscountText(product) }}</button></div>
			<div class="card-details"><button class="details">Detalhes</button></div>
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
		background-color: #0B1641
	}

	.card-title {
		font-size: 24px;
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
		font-size: 18px;
	}

	.card-price-original {
		font-size: 0.8rem;
		text-align: center;
		color: white;
		text-decoration: line-through;
		margin-top: 5px;
		font-family: 'Roboto';
		font-size: 12px;
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
		color: white;
		height: 39px;
		font-weight: bold;
		border: none;
		padding: 5px 10px;
		cursor: pointer;
		border-radius: 8px;
		font-family: 'Roboto';
		font-size: 18px;
	}
	button.details {
		background-color: #C70160;
		width : 116px;
	}

	button.discount {
		background-color: #16857B;
		width : 84px;

	}
</style>