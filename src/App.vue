<template>
  <div id="app">
    <div>
      <div class="add__container">
        <input
          class="add__input"
          type="text"
          v-model.trim="newTodo"
          placeholder="Buy milk"
          spellcheck="false"
          autofocus>
        <button
          v-on:click="addToDo"
          class="add__button">
          Add To Do
        </button>
      </div>

      <div class="add__filter">
        <label>Show completed?</label>
        <input
          v-model="showCompleted"
          id="checkbox"
          type="checkbox">
      </div>
    </div>

    <ul>
      <ToDoListItem
        v-bind:key="todo.id"
        v-for="todo in todos"
        v-if="todo.is_complete == false || showCompleted"
        v-bind:todo="todo">
      </ToDoListItem>
    </ul>
  </div>
</template>

<script>
import ToDoListItem from './components/ToDoListItem.vue'

export default {
  name: 'app',

  data: () => ({
    newTodo: '',
    todos: [
      { id: 1, name: 'Grocery shopping', is_complete: true },
      { id: 2, name: 'Call grandma', is_complete: false },
      { id: 3, name: 'Do CS 2254 homework', is_complete: false },
      { id: 4, name: 'Learn Vue.js', is_complete: false },
    ],
    showCompleted: false
  }),

  components: {
    ToDoListItem
  },

  methods: {
    addToDo () {
      var ids = this.todos.map(t => t.id)
      const nextId = Math.max(...ids) + 1
      const todo = { id: nextId, name: this.newTodo, is_complete: false }
      this.todos.push(todo)
      this.newTodo = ''
    }
  }
}
</script>

<style lang="scss">
$green: #42b983;
$white: #FFFFFF;
$black: #000000;
$gray: #EAEAEA;
$sans-serif: 'Avenir', Helvetica, Arial, sans-serif;
$border-radius: 3px;

#app {
  font: {
    family: $sans-serif;
    size: 16px;
  }
  color: #2c3e50;
  max-width: 25rem;
  margin: {
    top: 60px;
    right: auto;
    bottom: 0;
    left: auto;
  }
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
}

.add {
  &__container {
    display: flex;
    margin: {
      bottom: .5rem;
    }
  }

  &__filter {
    font: {
      size: .9rem;
    }
    padding: {
      left: .65rem;   
    }
  }

  &__input, &__button {
    border: {
      width: 1px;
      style: solid;
    }
  }

  &__input {
    flex: 8;
    padding: {
      top: .65rem;
      right: .65rem;
      bottom: .65rem;
      left: .65rem;   
    }
    font: {
      size: .95rem;
    }
    border: {
      color: $gray;
      top-left-radius: $border-radius;
      bottom-left-radius: $border-radius;
      right-width: 0;
    }
  }
  
  &__button {      
    flex: 2;
    color: $white;
    cursor: pointer;
    background: {
      color: $green;
    }
    font: {
      family: $sans-serif;
      size: .85rem;
      weight: 700;
    }
    padding: {
      top: .65rem;
      right: .65rem;
      bottom: .65rem;
      left: .65rem;
    }
    border: {
      color: darken($green, 5);
      top-right-radius: $border-radius;
      bottom-right-radius: $border-radius;
    }

    &:focus {
      outline: 0;
    }

    &:hover {
      // color: map-get($colors, font-color);
    }
  }
}

input {
  outline: 0;
}

ul {
  list-style-type: none;
  padding: 0;
}
</style>
