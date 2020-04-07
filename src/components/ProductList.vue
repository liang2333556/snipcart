<template>
  <section class="product-list">
    <h2>Welcome to my foods world~</h2>
    <ul class="products">
     <li v-for="(product,index) in products"
        :key="product.slug + '_' + index"
        @click="navigate($event, product)"
        class="product">
        <figure>
          <img :src="product.fields.image" class="img"/>
        </figure>
       <div  class="name">
          {{ product.fields.name }}
       </div>
        <p>
          <buy-button :product="product.fields" />
        </P>
     </li>
    </ul>
  </section>
</template>

<script>
import butter from '@/buttercms';
import BuyButton from './BuyButton';

export default {
  name: 'ProductList',
  components: {
    BuyButton,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    navigate($event, product) {
      if ($event.target.classList.contains('snipcart-add-item')) {
        return;
      }
      this.$router.push({
        name: 'Product',
        params: { slug: product.slug },
      });
    },
    getProducts() {
      butter.page.list('product')
        .then((res) => {
          this.products = res.data.data;
        });
    },
  },
  created() {
    // Fire on page creation
    this.getProducts();
  },
};
</script>

<style>
.product-list {
  margin-left: 200px;
}

.products {
  margin: 0;
  display: grid;
  grid-template-columns: 10fr 10fr 10fr;
  grid-gap: 100px;
}

.products p {
}

.products .snipcart-add-item {
  margin-top: 1em;
}

.product {
  list-style-type: none;
  box-sizing: border-box;
  width: 100%;
}

.product figure {
  margin: 100;
}
.img{
  width:200px;
  height:150px;
}
.product:hover {
  background-color: rgba(97, 189, 255, 0.34);
  cursor: pointer;
  border-radius: 20px;
}
  .name{
    text-align :center; }
</style>
