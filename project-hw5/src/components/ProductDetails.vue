<template>
    <div class="product-details">
      <h2>{{ product.name }}</h2>
      <p class="price">{{ product.price | formatPrice(currency) }}</p>
      <p class="availability">{{ availabilityText }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        product: {
          name: 'Example Product',
          price: 99.99,
          available: true,
        },
        currency: 'USD', 
      };
    },
    computed: {
      availabilityText() {
        return this.product.available ? 'Available' : 'Out of stock';
      },
    },
    filters: {
      formatPrice(value, currency) {
        let formattedPrice = value.toFixed(2);
        if (currency === 'RUB') {
          formattedPrice += ' ?';
        } else if (currency === 'EUR') {
          formattedPrice += ' ˆ';
        } else {
          formattedPrice = '$' + formattedPrice;
        }
        return formattedPrice;
      },
    },
  };
  </script>

<style lang="scss" scoped>
.product-details {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;

  h2 {
    font-size: 24px;
    margin-bottom: 10px;
    color: blue;
  }

  .price {
    font-size: 18px;
    font-weight: bold;
  }

  .availability {
    font-size: 16px;
  }
}
</style>