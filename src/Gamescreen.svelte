
<script>
import {onMount} from 'svelte';
let p
async function g(){
const r = await fetch('https://cameo-explorer.netlify.app/celebs.json/')
const res = await r.json()
const edited =await res.filter(x=>x.reviews>20)
const editeded =await edited.filter(x=>x.rating>3)
const final =await editeded.filter(x=>{
for(let i = 0;i<x.categories.length;i++){
if (x['categories'][i]==='athletes'){return x}
}})
console.log(final)
}
onMount(
p = g()
)
</script>
