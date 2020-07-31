<template>
  <form class="todo-form" @submit.prevent="submit">
    <input type="text" class="todo-form__field" placeholder="add details" v-model="text">
    <button class="todo-form__submit" type="submit">Add</button>
  </form>
</template>

<script>
export default {
  name: 'TodoAdd',
  data() {
    return {
      text: '',
    };
  },
  methods: {
    submit() {
      if (this.text.trim()) {
        this.$emit('submit', this.text);
        this.text = '';
      }
    },
  },
};
</script>

<style lang="scss">
  .todo-form {
    display: grid;
    grid-template-columns: 1fr min-content;
    column-gap: 20px;
    padding-top: 20px;
    padding-bottom: 20px;

    &__field {
      min-width: 0;
      padding: 10px 15px;
      background-color: transparent;
      border: 1px solid #eee;
      border-radius: 5px;
      font-size: 16px;
      outline: none;

      &:focus {
        border-color: #6da6f2;
      }
    }

    &__submit {
      border: 0;
      padding: 10px 20px;
      border-radius: 5px;
      font-size: 16px;
      font-weight: 600;
      background-color: #6da6f2;
      color: white;
      cursor: pointer;
      outline: none;

      &:hover,
      &:focus {
        background-color: darken(#6da6f2, 5%);
      }

      &:active {
        background-color: darken(#6da6f2, 10%);
      }
    }
  }
</style>
