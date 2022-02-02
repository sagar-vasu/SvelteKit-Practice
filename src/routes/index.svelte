<script context="module" >
    export async function load({fetch}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${'YOUR API KEY'}&language=en-US&page=1`)

        const data = await res.json();
        if(res.ok){
            return{
                props:{popular:data.results}
            }
        }
   }

   import global from "../global.css"
</script>

<script>
    import PopularMovies from "../components/popularMovies.svelte";
    import SearchMovies from "../components/searchMovies.svelte";
    import {fly} from "svelte/transition"
    export let popular;
</script>


<section

in:fly={{y:50, duration:500,delay:500}}
out:fly={{y:50,duration:500}}
>
    <SearchMovies />
    <PopularMovies movies = {popular} />
</section>

