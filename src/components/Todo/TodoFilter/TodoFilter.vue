<template>
  <div class="todo-filter">
    <button v-for="(item, id) in filters" :key="id"
      type="button"
      class="todo-filter__btn"
      :class="{['todo-filter__btn--active']: btnActive === item.key}"
      @click="toggleActive(item.key)"
    >
      {{item.value}}
    </button>
  </div>
</template>

<script>
export default {
  name: 'TodoFilter',
  data() {
    return {
      btnActive: this.filterActive,
    };
  },
  props: {
    filters: {
      type: Object,
    },
    filterActive: {
      type: String,
      default: 'all',
    },
  },
  methods: {
    toggleActive(val) {
      this.btnActive = val;
      this.$emit('filter', val);
    },
  },
};
</script>

<style lang="scss">
.todo-filter {
  display: flex;
  align-items: flex-end;
  box-shadow: inset 0 -1px 0 #eeeeee;

  &__btn {
    flex: 1 1 0;
    display: inline-block;
    padding: 15px 10px;
    position: relative;
    background-color: transparent;
    border: 0;
    margin: 0;
    outline: none;
    min-width: 80px;
    font-size: 14px;
    overflow: hidden;
    cursor: pointer;

    &::before {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      margin-left: auto;
      margin-right: auto;
      max-width: 70px;
      height: 5px;
      border-top-left-radius: 5px;
      border-top-right-radius: 5px;
      background-color: #6da6f2;
      transform: translateY(100%);
      transition: transform 200ms ease, opacity 150ms ease;
    }

    &:hover {
      &::before {
        transform: translateY(70%);
      }
    }

    &--active {
      pointer-events: none;
      &::before {
        transform: translateY(0);
      }
    }
  }
}
</style>
