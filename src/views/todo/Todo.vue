<template>
  <div class="todo">
    <h1>
      {{ title }}
    </h1>
    <ul class="todo__list">
      <li class="todo__item" v-for="(todo, index) in todos" :key="index">
        <input
          type="text"
          :class="{
            todo__content: true,
            content: true,
            content__checked: todo.checked,
          }"
          v-model="todo.content"
        />
        <div class="todo__actions">
          <Button @click="checkTodo(index)">
            <div class="todo__button todo__button--check">
              <svg
                height="512pt"
                viewBox="0 -21 512.016 512"
                width="512pt"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M234.668 469.34C105.281 469.34 0 364.063 0 234.676S105.281.008 234.668.008c44.992 0 88.766 12.82 126.59 37.097 7.426 4.782 9.601 14.68 4.82 22.125-4.797 7.446-14.676 9.598-22.121 4.82-32.64-20.972-70.441-32.042-109.289-32.042C122.922 32.008 32 122.93 32 234.676c0 111.742 90.922 202.664 202.668 202.664 111.742 0 202.664-90.922 202.664-202.664 0-6.68-.32-13.293-.937-19.797-.852-8.813 5.59-16.621 14.378-17.473 8.832-.812 16.618 5.59 17.473 14.38a239.63 239.63 0 011.086 22.89c0 129.387-105.277 234.664-234.664 234.664zm0 0"
                />
                <path
                  d="M261.332 288.008c-4.094 0-8.191-1.559-11.305-4.692l-96-96c-6.25-6.253-6.25-16.386 0-22.636s16.383-6.25 22.633 0l84.695 84.695 223.336-223.34c6.254-6.25 16.387-6.25 22.637 0s6.25 16.383 0 22.633L272.66 283.336a16.03 16.03 0 01-11.328 4.672zm0 0"
                />
              </svg>
            </div>
          </Button>
          <Button @click="deleteTodo(index)">
            <div class="todo__button todo__button--delete">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 407.521 407.521"
              >
                <path
                  d="M335.94 114.944H71.581a10.45 10.45 0 00-7.837 2.612 8.88 8.88 0 00-2.612 7.837l27.167 236.669c3.186 26.093 25.436 45.647 51.722 45.453h131.657c27.026.385 49.791-20.104 52.245-47.02l22.465-236.147a8.882 8.882 0 00-2.612-6.792 10.446 10.446 0 00-7.836-2.612zM303.026 359.45c-1.642 15.909-15.366 27.803-31.347 27.167H140.022c-15.694.637-29.184-11.024-30.825-26.645l-26.122-224.13h241.371l-21.42 223.608zM374.079 47.026H266.454V30.307c.58-16.148-12.04-29.708-28.188-30.288a29.104 29.104 0 00-1.591-.014h-65.829c-16.156-.299-29.494 12.555-29.793 28.711-.01.53-.005 1.061.014 1.591v16.718H33.442c-5.771 0-10.449 4.678-10.449 10.449s4.678 10.449 10.449 10.449h340.637c5.771 0 10.449-4.678 10.449-10.449s-4.679-10.448-10.449-10.448zM245.556 30.307v16.718h-83.592V30.307a8.36 8.36 0 018.881-9.404h65.829a8.359 8.359 0 018.882 9.404z"
                />
              </svg>
            </div>
          </Button>
        </div>
      </li>
    </ul>
    <Button @click="addTodo()">
      <div class="add__todo">
        New todo
      </div>
    </Button>
  </div>
</template>

<script>
import "./todo.scss";
import Button from "@/components/button";

export default {
  components: {
    Button,
  },
  data() {
    return {
      title: "Todo list",
      todos: [],
    };
  },
  methods: {
    deleteTodo(index) {
      console.log("delete todo", index);
      this.todos.splice(index, 1);
    },
    checkTodo(index) {
      this.todos[index].checked = !this.todos[index].checked;
    },
    addTodo() {
      const newTodo = {
        content: "",
        checked: false,
      }
      this.todos.push(newTodo);
    }
  },
};
</script>
