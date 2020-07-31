<template>
  <div class="todo-item">
    <label class="todo-item__checkbox">
      <input
        type="checkbox"
        class="todo-item__input"
        v-model="completed"
        @change="$emit('change', id)"
      >
      <span class="todo-item__icon">✓</span>
      <span class="todo-item__text" :class="{['todo-item__text--done'] :completed}">
        {{ title }}
      </span>
    </label>
    <button v-if="canRemove" class="todo-item__remove" @click="$emit('remove', id)">X</button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  data() {
    return {
      completed: this.done,
    };
  },
  props: {
    id: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    done: {
      type: Boolean,
      required: true,
    },
    canRemove: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss">
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 10px;
  margin-bottom: 10px;

  &__checkbox {
    display: flex;
    align-items: baseline;
    cursor: pointer;
    user-select: none;
  }

  &__input {
    margin: 0;
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    border: 0;
    padding: 0;
    clip: rect(0 0 0 0);
    overflow: hidden;
  }

  &__icon {
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    width: 25px;
    height: 25px;
    margin-right: 10px;
    border: 1px solid #eee;
    border-radius: 5px;
    font-size: 0.8em;
    color: transparent;
  }

  &__input:checked ~ &__icon {
    background-color: #6da6f2;
    border-color: #6da6f2;
    color: white;
  }

  &__text {
    flex: 1 1 0;
    text-align: left;
    &--done {
      text-decoration: line-through;
    }
  }

  &__remove {
    flex-shrink: 0;
    border: 0;
    width: 25px;
    height: 25px;
    border-radius: 5px;
    font-size: .8em;
    font-weight: 600;
    background-color: crimson;
    color: white;
    cursor: pointer;
    outline: none;

    &:hover,
    &:focus {
      background-color: darken(crimson, 5%);
    }

    &:active {
      background-color: darken(crimson, 10%);
    }
  }
}
</style>
