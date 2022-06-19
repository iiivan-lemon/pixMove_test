<template>
  <div class="product-list">
    <!--    лучше v-for использовать с key для поддержания внутреннего состояния компонента -->
    <div class="card" :key="product.id" v-for="product in products" :style="{width: cardsWidth + '%'}">
      <p class="card-title">{{ product.title }}</p>
      <img class="card-image" :src="product.image" alt="">
      <p class="card-price">Цена: {{ product.price }} {{ currency }}</p>

      <div>
        <input type="number" ref="amount" :id="product.id" >
        <span>кг</span>
      </div>

      <button class @click="addToCart(product)">В корзину</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    currency: String,
  },
  data() {
    return {
      products: [],
    };
  },
  computed: {
    cardsWidth() {
      // лучше в стилях адаптивность настраивать, чтобы не вытаскивать необходимые свойства из гл.переменной window
      // данный блок не работает потому что width = "число" без ед.изм.
      // let width = window.innerWidth;
      // let count = 1;
      // if (width > '840px') {
      //   count = 3;
      // } else if ((width > '420px' && width < '840px')) {
      //   count = 2;
      // }
      //return 100 / count;
    },
  },
  methods: {
    startPricesMonitoring() {
      // при первом открытии страницы происходил таймаут
      // до 1-ого таймаута вызываем getList

      this.getList();
      setInterval(() => {
        this.getList();
      }, 2000);
    },
    async getList() {
      // let data = await this.$store.dispatch('getProductsList');

      this.products = await this.$store.dispatch('getProductsList');
    },
    addToCart(product) {
      // необходима валидация значений - написал проверку amount > 0 чтобы любое невалидное значение не добавлялось в корзину
      const amount = this.$refs.amount.find((input) => {
        return (input.id === product.id)
      }).value;
      if (Number(amount) > 0) {
        this.$parent.cart.push({
          amount: Number(amount),
          price: product.price,
          title: product.title,
        });
      }
    },
  },
  created() {
    this.startPricesMonitoring();
  },
};
</script>


<!--стоит  использовать css модули и препроцессоры css  для инкапсуляции и удобства написания стилей для каждого компонента  -->
<style>
@import "list.css";
</style>
