
<template>
  <div>
    <Header />
    <main>
      <h1>¡Hola desde Vue 3 en Laravel!</h1>
      <slot />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from './Header.vue';
import Footer from './Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Footer
  }
};
</script>

<style scoped>
main {
  min-height: 80vh;
  padding: 2rem;
}
</style>
