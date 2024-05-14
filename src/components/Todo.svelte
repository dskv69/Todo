<script>
	export let text;
	export let id;
	let show = false;
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
	const deleteHandler = () => {
		dispatch('deleteTodo', { id });
	};

	const doneHandler = () => {
		dispatch('doneTodo', { id });
	};

	const showDetails = () => {
		show = !show;
	};
</script>

<div id="TodoItemDiv">
	<span id="TodoText">{text}</span>
	<div id="ButtonsContainer">
		<button id="ButtonDelete" on:click={deleteHandler}>Delete</button>
		<button id="ButtonDone" on:click={doneHandler}>Done</button>
	</div>
</div>

<style>
	#TodoItemDiv {
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 10px;
	}

	#TodoText {
		width: 100%;
		color: white;
		font-weight: 500;
		font-size: larger;
		text-align: left;
		text-wrap: balance;
		display: inline-block;
		word-break: break-all;
	}

	#ButtonsContainer {
		text-align: right;
		width: 50%;
	}

	button {
		color: white;
	}

	#ButtonDelete {
		background-color: #e86f6f;
		border: none;
		width: 50px;
		height: 30px;
		cursor: pointer;
	}

	#ButtonDelete:hover {
		background-color: #b64141;
	}

	#ButtonDone {
		background-color: #74ff8b;
		border: none;
		width: 50px;
		height: 30px;
		cursor: pointer;
	}

	#ButtonDone:hover {
		background-color: #63b83b;
	}
</style>
