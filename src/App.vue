<template>
  <div id="app">
    <Todo />
    <div class="footer">
      <p class="footer__text">
        Victor Hripko @DevChallenges.io
      </p>
    </div>
  </div>
</template>

<script>
import Todo from '@/components/Todo/Todo.vue';

export default {
  components: {
    Todo,
  },
};
</script>

<style lang="scss">
*, *::before, *::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.footer {
  margin-top: auto;
  padding: 10px 20px;
  text-align: center;
  background-image: linear-gradient(#ddd, #ddd);
  background-size: 400px 1px;
  background-repeat: no-repeat;
  background-position: center top;

  &__text {
    color: #ddd;
  }
}
</style>
