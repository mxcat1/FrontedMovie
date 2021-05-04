<script context="module">

    let apikey='a47cfe9dac8628fa1dc279e89f074d2a'
    let pathUrl=`https://api.themoviedb.org/3/movie/popular?api_key=${apikey}&language=es-ES&page=1`
    export function preload() {
        return this.fetch(pathUrl).then(r => r.json()).then(peliculas => {
            return { peliculas };
        });
    }
</script>

<script>

    import CardPelicula from '../components/cardMovieComponent.svelte'
    import GridPeliculas from '../components/gridMoviesComponent.svelte'
    export let peliculas;

</script>

<style>

    h1 {
        font-size: 2.8em;
        text-transform: uppercase;
        font-weight: 700;
        margin: 0 0 0.5em 0;
    }

    p {
        margin: 1em auto;
    }

    @media (min-width: 480px) {
        h1 {
            font-size: 4em;
        }
    }
</style>

<svelte:head>
    <title>MovieView</title>
</svelte:head>


<h1>Peliculas mas Populares</h1>
<GridPeliculas>
    {#each peliculas.results as pelicula}
        <CardPelicula imgPelicula={pelicula.poster_path} idPelicula={pelicula.id} altPelicula={pelicula.title} tituloPelicula={pelicula.title} descripcionPelicula={pelicula.overview}/>
    {:else}
        <p>loading...</p>
    {/each}
</GridPeliculas>