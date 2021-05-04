<script context="module">
    let apikey = 'a47cfe9dac8628fa1dc279e89f074d2a'
    let pathUrl = `https://api.themoviedb.org/3/discover/movie?api_key=${apikey}&language=es-ES&sort_by=original_title.asc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=free`

    export function preload() {
        return this.fetch(pathUrl).then(r => r.json()).then(listaPeliculas => {
            return {listaPeliculas};
        });
    }
</script>

<script>

    import CardPelicula from '../../components/cardMovieComponent.svelte'
    import GridPeliculas from '../../components/gridMoviesComponent.svelte'
    import InputPelicula from '../../components/buscadorMoviesComponent.svelte'

    export let listaPeliculas

    let buscarpelicula

    async function nuevoevento(event) {
        if (event.detail.codekey === 13) {
            let pathUrl = `https://api.themoviedb.org/3/search/movie?api_key=a47cfe9dac8628fa1dc279e89f074d2a&language=en-US&query=${buscarpelicula}&page=1&include_adult=false`
            const res = await fetch(pathUrl);
            const data = await res.json();
            listaPeliculas = data
        }

    }
</script>
<style>
    h1 {
        font-size: 2.8em;
        text-transform: uppercase;
        font-weight: 700;
        margin: 0 0 0.5em 0;
    }
</style>
<svelte:head>
    <title>Peliculas</title>
</svelte:head>

<h1>Todas las Peliculas</h1>
<InputPelicula bind:value={buscarpelicula} on:enter={nuevoevento}/>
<GridPeliculas>
    {#each listaPeliculas.results as pelis}
        <CardPelicula imgPelicula={pelis.poster_path} idPelicula={pelis.id} altPelicula={pelis.title}
                      tituloPelicula={pelis.title}/>
    {:else}
        <p>Cargando....</p>
    {/each}
</GridPeliculas>