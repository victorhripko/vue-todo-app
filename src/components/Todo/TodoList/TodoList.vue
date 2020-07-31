<template>
  <div class="todo-list">
    <TodoItem v-for="item in todoItems" :key="item.id"
      :id="item.id"
      :title="item.title"
      :done="item.done"
      :canRemove="active === 'completed' && item.done"
      @change="emitId"
      @remove="remove"
    />
    <button
      class="todo-list__clear"
      v-if="active === 'completed' && todoItems.length"
      @click="$emit('clear')"
    >
      REMOVE ALL
    </button>
  </div>
</template>

<script>
import TodoItem from '@/components/Todo/TodoItem/TodoItem.vue';

export default {
  name: 'TodoList',
  props: {
    todos: {
      required: true,
    },
    active: {
      type: String,
    },
  },
  computed: {
    todoItems() {
      if (this.active === 'completed') {
        return this.todos.filter((el) => el.done);
      } if (this.active === 'active') {
        return this.todos.filter((el) => !el.done);
      }
      return this.todos;
    },
  },
  components: {
    TodoItem,
  },
  methods: {
    emitId(id) {
      this.$emit('change', id);
    },
    remove(id) {
      this.$emit('remove', id);
    },
  },
};
</script>

<style lang="scss">
.todo-list {
  display: flex;
  flex-direction: column;

  &__clear {
    border: 0;
    margin-left: auto;
    padding: 10px 20px;
    border-radius: 5px;
    font-size: 16px;
    font-weight: 600;
    background-color: red;
    color: white;
    cursor: pointer;
    outline: none;

    &:hover,
    &:focus {
      background-color: darken(red, 5%);
    }

    &:active {
      background-color: darken(red, 10%);
    }
  }
}
</style>
