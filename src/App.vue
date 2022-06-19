<template>
  <div id="app">
    <!--    должны одинаково описаны компоненты-->
    <!--    <Header :cart="cart" :currency="currency"></Header>-->
    <!--    <List :currency="currency"/>-->
    <!--    <Cart :cart="cart"/>-->
    <Header :cart="cart" :currency="currency"></Header>
    <List :currency="currency"></List>
    <Cart :cart="cart"></Cart>
  </div>
</template>

<script>
import Header from './components/header/Header.vue';
import List from './components/list/List.vue';
import Cart from './components/cart/Cart.vue';

export default {
  name: 'App',
  data() {
    return {
      cart: [],
      currency: 'VGTB',
    };
  },
  components: {
    Header,
    List,
    Cart,
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--font-color);
}

:root {
  --font-color: #2c3e50;
  --color-border-card: #908888;
  --header-color: #e5e5e5;
}
</style>
