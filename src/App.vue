<template>
  <div
    class="
      wrapper
      min-h-screen
      bg-blue-50
      flex
      justify-center
      items-center
      mx-auto
    "
  >
    <div
      class="
        wrapper
        border-2
        border-green-600
        rounded-lg
        h-3/4
        w-4/5
        sm:w-2/5
        md:w-2/5
        bg-blue-50
        flex
        flex-col
        justify-between
      "
    >
      <Header />
      <ShoppingList />
      <Footer />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import ShoppingList from './components/ShoppingList.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    ShoppingList,
    Footer,
  },
};
</script>

<style lang="scss">
#app {
  padding: 2rem 0;
  background: #EFF6FF;
}

.wrapper {
  font-family: 'Urbanist', sans-serif;
}
</style>
