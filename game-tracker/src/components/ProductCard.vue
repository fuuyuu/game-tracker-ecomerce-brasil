<template>
  <div class="card-container">
    <div class="card">
      <div class="card-image">
        <img :src="product.thumb || fallbackImage" alt="{{ product.title }}">
      </div>
      <div class="card-content">
        <div class="card-title">{{ product.title }}</div>
        <div class="card-price">
			<div class="card-price-original">$ {{ product.normalPrice }}</div>
			<div class="card-price-current">$ {{ product.salePrice }}</div>
			<div class="card-discount"><button class="discount">{{ getDiscountText(product) }}</button></div>
			<div class="card-details"><button class="details">DETALHES</button></div>
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
	data() {
		return {
			fallbackImage: require('@/assets/logo/sem-imagem.jpg'),
		}
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

<style>
	@import "@/components/css/ProductCard.css";
</style>