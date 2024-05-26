<svelte:options immutable={true} />

<script>
	import Button from './Button.svelte';
	import { createEventDispatcher } from 'svelte';

	export let todos = [];
	let inputText = '';

	const dispatch = createEventDispatcher();

	function handleAddTodo() {
		const isNotCancelled = dispatch(
			'addtodo',
			{
				title: inputText
			},
			{ cancelable: true }
		);
		if (isNotCancelled) {
			inputText = '';
		}
	}
</script>

<div class="todo-list-wrapper">
	<ul class="no-bullets">
		{#each todos as { id, title }, index (id)}
			{@const number = index + 1}
			<li>{number}- {title}</li>
            
		{/each}
	</ul>
    <br>
	<form class="add-todo-form" on:submit|preventDefault={handleAddTodo}>
		<input class="input-form" bind:value={inputText} placeholder="Escribe item nuevo"/>
		<br>
        <br>
        <Button bgColor="green" type="submit" disabled={!inputText}>Agregar item</Button>
	</form>
</div>
<style>
ul.no-bullets{
  list-style-type: none;
  color: black;
  font-size: 18px;
  margin: 0%;
  padding: 0%;
  text-align: left;
}
.input-form{
padding: 10px;
background-color: black;
color:white;
border-color: blue;
border: 2px;
font-size: 16px;
font-weight: bold;
float:left;

}
</style>