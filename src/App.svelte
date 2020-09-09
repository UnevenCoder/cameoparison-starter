<script>
import Game from './Gamescreen.svelte'
import Welcome from './Welcome.svelte'
    let a,b,slug
	let state ='welcome'
	const start = (e)=>{
	slug = e.detail.category.slug
	state='playing'
}
$: b={a:slug}
</script>
<main>
	{#if state === 'welcome'}
	<Welcome on:select={start}/>
	{:else if state == 'playing'}
<p>This is game screen</p>

<Game {b}/>
     {/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 600px;
		margin: 0 auto;
		display:flex;
		flex-direction:column;
		align-items:center;
	}

</style>