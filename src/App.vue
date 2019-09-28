<template>
  <div>
    <todo-header></todo-header>
    <todo-input v-on:add="addTodoItem"></todo-input>
    <todo-list :items="todoItems" v-on:remove="removeItem"></todo-list>
    <todo-footer v-on:clear="clearTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';
export default {
	components: {
		TodoHeader,
		TodoInput,
		TodoList,
		TodoFooter,
	},
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		addTodoItem: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		fetchTodoItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				var item = localStorage.key(i);
				this.todoItems.push(item);
			}
		},
		removeItem: function(index, todoItem) {
			this.todoItems.splice(index, 1);
			localStorage.removeItem(todoItem);
		},
		clearTodoItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	created: function() {
		this.fetchTodoItems();
	},
};
</script>

<style>
</style>
