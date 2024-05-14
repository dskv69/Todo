<script>
	import { json } from '@sveltejs/kit';
	import CompletedTodo from '../components/CompletedTodo.svelte';
	import CreateTodo from '../components/CreateTodo.svelte';
	import Todo from '../components/Todo.svelte';
	import '../style.css';
	import { onMount } from 'svelte';

	let todos = [];
	let completed = [];
	let main;

	const addTodo = (event) => {
		todos = [{ id: todos.length, text: event.detail.text }, ...todos];
		localStorage.setItem('todos', JSON.stringify(todos));
	};

	const findIndex = (id) => {
		for (let i = 0; i < todos.length; i++) {
			if (id == todos[i].id) {
				return i;
			}
		}
	};

	const deleteTodo = (event) => {
		let index = findIndex(event.detail.id);
		todos.splice(index, 1);
		todos = [...todos];
		localStorage.setItem('todos', JSON.stringify(todos));
	};

	const doneTodo = (event) => {
		let index = findIndex(event.detail.id);
		let complet = todos[index];
		complet.id = completed.length;
		completed = [...completed, complet];
		todos.splice(index, 1);
		todos = [...todos];
		localStorage.setItem('todos', JSON.stringify(todos));
		localStorage.setItem('completed', JSON.stringify(completed));
	};

	onMount(() => {
		let todosStored = JSON.parse(localStorage.getItem('todos'));
		let completedStored = JSON.parse(localStorage.getItem('completed'));
		if (todosStored) {
			if (todosStored.length != 0) {
				todos = todosStored;
			}
		}

		if (completedStored) {
			if (completedStored.length != 0) {
				completed = completedStored;
			}
		}
	});
</script>

<main style="height: 2000px;" bind:this={main}>
	<div id="containercontainer">
		<div id="container">
			<CreateTodo on:submitTodo={addTodo} />
			{#if todos.length > 0}
				{#each todos as todo (todo.id)}
					<div id="todos">
						<div id="todos2">
							<Todo
								on:doneTodo={doneTodo}
								on:deleteTodo={deleteTodo}
								text={todo.text}
								id={todo.id}
							/>
						</div>
					</div>
				{/each}
			{:else}
				<h1 style="color: aliceblue;">Nothing Todo :)</h1>
			{/if}
		</div>
	</div>

	<CompletedTodo {completed} />
</main>
