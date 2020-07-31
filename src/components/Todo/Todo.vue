<template>
  <div class="todo">
    <h1 class="todo__title">
      #todo
    </h1>
    <TodoFilter :filters="filters" @filter="filter"/>
    <TodoAdd @submit="addItem" />
    <TodoList
      :active="active"
      :todos="todos"
      @change="toggleItem"
      @clear="clear"
      @remove="clearItem"
    />
  </div>
</template>

<script>
import TodoFilter from './TodoFilter/TodoFilter.vue';
import TodoAdd from './TodoAdd/TodoAdd.vue';
import TodoList from './TodoList/TodoList.vue';

export default {
  name: 'Todo',
  data() {
    return {
      todos: [],
      active: 'all',
      filters: [
        {
          key: 'all',
          value: 'All',
        },
        {
          key: 'active',
          value: 'Active',
        },
        {
          key: 'completed',
          value: 'Completed',
        },
      ],
    };
  },
  components: {
    TodoFilter,
    TodoAdd,
    TodoList,
  },
  methods: {
    addItem(title) {
      this.todos.push({
        id: Date.now(),
        title,
        done: false,
      });
    },
    toggleItem(id) {
      this.todos.map((el) => {
        const item = el;

        if (item.id === id) {
          item.done = !item.done;
        }

        return item;
      });
    },
    filter(val) {
      this.active = val;
    },
    clear() {
      this.todos = this.todos.filter((i) => !i.done);
    },
    clearItem(id) {
      this.todos = this.todos.filter((el) => (el.id !== id));
    },
  },
};
</script>

<style lang="scss">
  .todo {
    max-width: 500px;
    margin-left: auto;
    margin-right: auto;

    &__title {
      margin-bottom: 20px;
      text-align: center;
    }
  }
</style>
