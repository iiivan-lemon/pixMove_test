<!--<script>-->
<!--export default {-->
<!--  name: 'Header',-->
<!--  props: {-->
<!--    cart: Array,-->
<!--    required: true,-->
<!--    default: {},-->

<!--    currency: String,-->
<!--  },-->
<!--  data() {-->
<!--    return {-->
<!--      cartPrice: 0,-->
<!--    };-->
<!--  },-->
<!--  watch: {-->
<!--    cart(cart) {-->
<!--      let val = 0;-->
<!--      cart.forEach((item) => {-->
<!--        val += item.price * item.amount;-->
<!--      });-->
<!--      this.cartPrice = val;-->
<!--    },-->
<!--  },-->
<!--}-->
<!--</script>-->

<!--<style scoped>-->
<!--  .header {-->
<!--    padding: 10px;-->
<!--    background: var(&#45;&#45;header-color);-->
<!--  }-->
<!--</style>-->

<!--порядок тегов должен быть одинаковый для всех компонентов-->
<!--style всегда последний -->

<template>
  <div class="header">
    <h3>Товаров в корзине на: {{ cartPrice }} {{ currency }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    cart: Array,
    required: true,
    default: {},

    currency: String,
  },
  data() {
    return {
      cartPrice: 0,
    };
  },
  watch: {
    cart(cart) {
      let val = 0;
      cart.forEach((item) => {
        val += item.price * item.amount;
      });
      this.cartPrice = val;
    },
  },
}
</script>

<style>
  @import "header.css";
</style>