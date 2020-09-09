
<script>
import {onMount} from 'svelte';
let p 
export let b
let global_data

  async function g(slug){
    fetch('https://cameo-explorer.netlify.app/celebs.json/')
    .then(r => r.json())
    .then(r => {
let shuffled = r.map((a) => ({sort: Math.random(), value: a}))
                .sort((a, b) => a.sort - b.sort)
                .map((a) => a.value)
global_data = shuffled
        .find(x => (
          x.reviews > 20 &&
          x.rating > 3 &&
          x.categories.includes(slug)
        ));
    });
  }

  onMount(() => {
    g('athletes');
  });

</script>
{global_data?global_data.name:'loading'}

{b.a}
<main>
<header>
<p>Tap on the more monetisable celebrity's face, or tap 'same price' if society values them equally.</p>
</header>
 <div class="game-container">


 </div>
</main>

 <style>
header {
    display: block;
}
p {
    line-height: 1.5;
}
main{
width:100vw;
height:1000vh;
display:flex;
flex-direction:column;
}
 </style>