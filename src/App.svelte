<script>
	export let name;
	let src = 'DMR_120.jpg';
	import Nested from './nested.svelte';
	import HTMLString from './HTMLString.svelte';
	let count = 0;
	$: doubled = count*2;

	function handleClick(){
		count+=1;
	}
	import Info from './Info.svelte';

	const pkg = {
		name: 'svelte',
		version: 3,
		speed: 'blazing',
		website: 'https://svelte.dev'
	};

	let user = {loggedIn : false};
	function toggleLogin(){
		user.loggedIn = !user.loggedIn;
	}

	let navLinks = [
		{url:"http://www.google.com",label:"google"},
		{url:"http://www.amazon.fr",label:"amazon"}
	]

	import Inner from './Inner.svelte';

	function handleInnerMessage(event){
		alert(event.detail.text);
	}
</script>

<main>
	<nav>
		<ul>
			{#each navLinks as {url,label}}
			<li><a href={url}>{label}</a></li>
			{/each}
		</ul>
	</nav>
	<h1>Hello {name}!</h1>
	<img {src} alt="NAS with play button">
	<Nested property="toto"/>
	<HTMLString />
	<button on:click={handleClick}>incremented me {count} {count < 2 ? 'time' : 'times'}</button>
	<p>reactive propagation : {doubled}</p>
	<Info {...pkg}/>
	{#if user.loggedIn}
	<button on:click={toggleLogin} class="login">
		Log out
	</button>
	{:else}
	<button on:click={toggleLogin} class="login">
		Log in
	</button>
	{/if}

	<Inner on:message={handleInnerMessage}/>
</main>

<style>

	ul {
		overflow: hidden;
  		background-color: #333;
		list-style-type: none;
		margin: 0;
		padding: 0;
		height: 60px;
	}
	li{
		display: inline;
	}
	a{
		position: relative;
		height: 60px;
		padding: 20px;
	}
	.login{
		position: absolute;
		right: 20px;
		top: 20px;
	}
	main {
		text-align: center;
		padding: 0;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	img{
		height: 50px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>