<script>
import {createEventDispatcher} from 'svelte'
const dispatch = createEventDispatcher();
let clicked=false;
function work(category){
console.log('selected',category)
clicked=true;
dispatch('select',{category});
}
const categories = [
{slug:'actors',label:'Actors'},
{slug:'athletes',label:'Athletes'},
{slug:'comedians',label:'Comedians'},
{slug:'creators',label:'Creators'},
{slug:'models',label:'Models'},
{slug:'musicians',label:'Musicians'},
{slug:'reality-tv',label:'Reality TV'}
]
</script>
<header>
    <h1 >
		CameoP<span class="logo">a</span>rison
	</h1> 

	<p >
		On <a href="https://cameo.com">cameo.com</a>, you can buy personalised video clips from everyone from Lindsay Lohan to Ice T.
	</p> 

	<p >But who commands the highest price?</p>
</header>
<p >Pick a category to play a game:</p>
<div class="categories ">
{#each categories as c}
<button disabled={clicked} on:click={()=>work(c)}>{c.label}</button>
{/each}
</div>
<style>
h1{
    color: #ff3e00;
    text-transform: uppercase;
    font-size: min(12vw, 4em);
    font-weight: 100;
    margin: 0 0 0.5em 0;}
.logo{
    display: inline-block;
    background: url(/icons/compare.svg) 50% 50% no-repeat;
    background-size: 100% 100%;
    width: 0.8em;
    top: 0.05em;
    transform: scale(1.4);
    left: 0.02em;
    text-indent: -9999px;
}
p{
    max-width: 24em;
    margin: 0 auto 1em auto;
    line-height: 1.5;
}
.categories{
display:inline;
width:100%;
height:auto;

}
button {
    padding: 1em;
    margin-right:10px;
    margin-right:15px;
    width: auto;
}
</style>