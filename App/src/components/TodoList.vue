<script>
import TodosDoneCheck from './TodosDoneCheck.vue';

export default {
  data() {
    return {
      todos: [],
      newTodo: ""
    };
  },

  components: {
    TodosDoneCheck
  },

  computed: {
    totalDone() {
      return this.todos.filter(todo => todo.isDone).length;
    }
  },

  mounted() {
    const savedTodos = localStorage.getItem('todos');
    if (savedTodos) {
      this.todos = JSON.parse(savedTodos);
    }
  },

  watch: {
    todos: {
      handler(newTodos) {
        localStorage.setItem('todos', JSON.stringify(newTodos));
      },
      deep: true
    }
  },

  methods: {
    toggle(todo) {
      todo.isDone = !todo.isDone;
    },
    add() {
      if (!(this.newTodo)) {
        return;
      }
      this.todos.push({
        title: this.newTodo,
        createDate: new Date(),
        note: "",
        isDone: false
      });
      this.newTodo = "";
    },
    remove(index) {
        this.todos.splice(index, 1);
    }
  }
};
</script>

<template>
  <div class="todo-list">
    <div class="input-group mb-3">
      <input type="text" v-model="newTodo" class="form-control" placeholder="Добавьте новую задачу" @keyup.enter="add" />
      <button class="btn btn-outline-secondary" type="button" @click="add">
        Добавить
      </button>
    </div>

    <ul class="list-group todo-grid">
      <li
        v-for="(item, index) in todos"
        class="list-group-item todo-card"
        :class="{done: item.isDone}"
      >
        <div class="input-group">
          <div class="input-group-text">
            <input
              v-model="item.isDone"
              class="form-check-input mt-0"
              type="checkbox"
              @click="toggle(item)"
            />
            <span class="todo-title" @click="toggle(item)">
            {{ item.title }}
          </span>
          </div>
          <textarea
            v-model="item.note"
            class=" todo-textarea"
            placeholder="Добавьте заметку к задаче"
          ></textarea>
          <button
            class="btn btn-outline-secondary"
            
            type="button"
            @click="remove(index)"
          >
            X
          </button>
        </div>
      </li>
    </ul>
  </div>
  <todos-done-check :total-done="totalDone"/>
</template>

<style>
.todo-list {
  margin: 20px;
}
.todo-title {
  flex: 1;
}
.todo-textarea {
  min-width: 100px
}
.input-group {
  cursor: pointer;
}
.done .todo-title {
  text-decoration: line-through;
}
.todo-grid {
  display: grid;
  gap: 1rem;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  padding: 0;
  margin: 0;
}

.todo-card {
  min-height: 120px;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1rem;
  border-radius: 16px;
  border: 1px solid #ddd;
  background: #fff;
}

.todo-card .input-group {
  flex-direction: column;
  gap: 0.75rem;
}

.todo-card button {
  align-self: flex-end;
}

.todo-card .todo-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.todo-card .todo-slider {
  width: 100%;
}

.done .todo-title {
  text-decoration: line-through;
  opacity: 0.7;
}
</style>
