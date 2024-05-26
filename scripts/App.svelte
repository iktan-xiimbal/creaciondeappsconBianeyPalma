<script>
    import svelteLogo from './assets/svelte.svg'
    import viteLogo from '/vite.svg'
    import Counter from './lib/Counter.svelte'
    import Button from './lib/Button.svelte'
    import Header from './lib/Header.svelte'
    import List from './lib/List.svelte'
    import { v4 as uuid } from 'uuid';

   let todos = [
		{
			id: uuid(),
			title: 'Vestido',
			completed: true
		},
		{
			id: uuid(),
			title: 'Blusa',
			completed: false
		},
		{
			id: uuid(),
			title: 'Pantalón',
			completed: true
		}
	];

	function handleAddTodo(event) {
		// event.preventDefault();
		todos = [
			...todos,
			{
				id: uuid(),
				title: event.detail.title,
				completed: false
			}
		];
	}
</script>


  <Header />
  <img class="banner" src="web-banner.jpg" alt="a" /> 
  <h1>Bienvenida a mi página</h1>
  <h3>Agrega los items que quieras a esta lista de compras</h3>
  <div>
  <br>
 <List {todos} on:addtodo={handleAddTodo} />
 </div>
  <br>
  <div>
  <p class="read-the-docs">
    Recursos útiles para aprender a programar: <a href="https://codedamn.com/">Codedamn</a>, <a href="https://www.udemy.com/">Udemy</a>, y <a href="https://www.coursera.org/ ">Coursera</a>
  </p>
  </div>
  
  
  <style>
  :global(body){
    background-color: rgb(231, 214, 247)
  }
  h1{
    color: rgb(9, 11, 113);
  }
  h3{
    color:blue;
  }
  .banner{
    height: 300px;
  }
  .read-the-docs{
  color: blue;
    font-weight: bold;
  }
    
  </style>
  