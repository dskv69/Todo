<script>
	import { createEventDispatcher } from 'svelte';
	let todoInput = '';
	const dispatch = createEventDispatcher();

	const submitTodoHandler = (event) => {
		if (todoInput == '') {
			return;
		}
		event.preventDefault();
		dispatch('submitTodo', {
			text: todoInput
		});
		todoInput = '';
	};
</script>

<form on:submit={submitTodoHandler}>
	<input id="textInp" bind:value={todoInput} type="text" placeholder="Type your Todo" />
	<input type="submit" value="ADD" />
</form>

<style>
	form {
		width: 100%;
		margin-bottom: 25px;
	}

	input {
		width: 50px;
		height: 35px;
		margin: 0;
	}

	#textInp {
		width: 50%;
		height: 12px;
		margin: 0;
		padding: 10px;
		border-radius: 10px;
		border: 1px solid black;
	}
</style>
