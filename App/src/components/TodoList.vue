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
        createDate: new Date().toLocaleDateString('ru-RU'),
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
        Добавить задачу
      </button>
    </div>

    <ul class="list-group todo-grid">
      <li
        v-for="(item, index) in todos"
        class="list-group-item todo-card"
        :class="{done: item.isDone}"
      >
        <div class="input-group">
          <span class="date">Задача от {{ item.createDate }}</span>
          <span class="todo-title">
            {{ item.title }}
          </span>
          <textarea
            v-model="item.note"
            class="todo-textarea"
            placeholder="Добавьте заметку к задаче, её краткое описание или разбейте её на подзадачи"
          ></textarea>
          <button
            class="btn btn-outline-primary"
            type="button"
            @click="toggle(item)"
            v-if="item.isDone == false"
          >
            Сделать
          </button>
          <button
            class="btn btn-secondary"
            type="button"
            @click="toggle(item)"
            v-else
          >
            Отменить
          </button>
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
.date {
  font-size: 1rem;
  color: #888;
}
.todo-list {
  margin: 20px;
}
.todo-title {
  flex: 1;
}
.todo-textarea {
  field-sizing: content;
  max-height: 200px;
  scrollbar-width: auto;
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
  grid-template-columns: repeat(auto-fit, minmax(350px, auto));
  padding: 0;
  margin: 0;
}

.todo-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1rem;
  border-radius: 16px;
  border: 1px solid #ddd;
  background: #fff;
  min-height: auto;
  min-width: 350px;
  width: auto;
  max-width: 100%;
}


.todo-card .input-group {
  flex-direction: column;
  align-items: stretch;
  gap: 0.6rem;
}

.todo-card button {
  align-self: flex-end;
}

.todo-card .todo-title {
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}
.todo-title {
  word-break: break-word;
}
.todo-card .todo-slider {
  width: 100%;
}

.done .todo-title {
  text-decoration: line-through;
  opacity: 0.7;
}
</style>
