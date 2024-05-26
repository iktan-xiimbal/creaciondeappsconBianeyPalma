<script>
	export let size = 'small';
	export let shadow = false;
	export let bgColor = 'inherit';
	export let textColor = 'inherit';
	export let userName=undefined;
	
	let count=1;
	function printName(name) {
    	console.log("Hello", name);
		if (count === 2) {
			bgColor="green"} else{bgColor="blue"};
		count += 1;
  	}
</script>

<button
	on:click={() => printName({userName})}
	style:--buttonBgColor={bgColor}
	style:--buttonTextColor={textColor}
	class:size-lg={size === 'large'}
	class:size-sm={size === 'small'}
	class:shadow
	{...$$restProps}
	
>
	<slot>Boton</slot>
</button>

<style lang="scss">
	button {
		display: flex;
		align-items: center;
		border: none;
		background-color: var(--buttonBgColor);
		color: var(--buttonTextColor);
		font-weight: bold;
		border-radius: 5px;
		cursor: pointer;
		.left-content {
			margin-right: 10px;
		}
		&:hover {
			background-image: linear-gradient(rgba(0, 0, 0, 0.4) 0 0);
		}
		&:active {
			background-image: linear-gradient(rgba(255, 255, 255, 0.1) 0 0);
		}
		&.size-sm {
			padding: 10px 20px;
		}
		&.size-lg {
			padding: 20px 25px;
			font-size: 20px;
		}
		&.shadow {
			box-shadow: 0 0 10px rgba(1, 1, 1, 0.3);
		}
	}
</style>
