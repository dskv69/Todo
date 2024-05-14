<script>
	export let completed;
</script>

<div id="completedTodos">
	<div id="completedTodosIn">
		<h1 style="color: aliceblue; text-decoration: underline; margin: 10px;">Completed Todos</h1>
		{#if completed.length <= 0}
			<p style="color: #aaa; margin-top: 5px;">Nothing Completed :(</p>
		{/if}
		{#each completed as completedItem (completedItem.id)}
			<div class="completedTodoItem">
				<span>{completedItem.text}</span>
				<div id="undoContainer">
					<button id="undo">Del</button>
				</div>
			</div>
		{/each}
	</div>
</div>

<style>
	#completedTodos {
		width: 100%;
		text-align: center;
		display: flex;
		justify-content: center;
	}

	#completedTodosIn {
		box-shadow: 0 0 2px 2px rgba(0, 0, 0, 0.062);
		max-width: 700px;
		width: 90%;
		padding: 18px;
		border-radius: 10px;
		text-align: center;
		background-color: rgb(50, 92, 155);
		padding: 20px;
		min-height: 200px;
		display: flex;
		flex-direction: column;
	}

	.completedTodoItem {
		text-decoration: line-through;
		text-wrap: balance;
		display: flex;
		justify-content: center;
		align-items: center;
		word-break: break-all;
		background-color: aliceblue;
		margin: 10px;
		padding: 10px;
		border-radius: 10px;
		opacity: 50%;
		box-shadow: 0 0 2px 2px rgba(0, 0, 0, 0.397);
	}

	span {
		text-decoration: inherit;
		width: 100%;
	}

	#undoContainer {
		width: 50%;
	}

	#undo {
		width: 100px;
		height: 30px;
		border-radius: 10px;
		border: none;
		background-color: black;
		color: white;
	}

	#undo:hover {
		cursor: pointer;
		background-color: #242424;
	}

	.completedTodoItem:hover {
		text-decoration: none !important;
		/* font-size: larger; */
		font-weight: bolder;
		opacity: 100%;
		cursor: pointer;
	}
</style>
