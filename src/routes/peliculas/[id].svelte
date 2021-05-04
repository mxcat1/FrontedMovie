<script context="module">

    let apikey = 'a47cfe9dac8628fa1dc279e89f074d2a'


    export async function preload({params}) {
        let pathUrl = `https://api.themoviedb.org/3/movie/${params.id}?api_key=${apikey}&language=es-ES`
        let pathUrlvideo = `https://api.themoviedb.org/3/movie/${params.id}/videos?api_key=${apikey}&language=en-EN`
        const res = await this.fetch(pathUrl);
        const resvideo = await this.fetch(pathUrlvideo);
        const data = await res.json();
        const datavideo = await resvideo.json();

        if (res.status === 200) {
            return {peliculavideo: datavideo, peliculadesc: data};
        } else {
            this.error(res.status, data.message);
        }
    }
</script>

<script>
    export let peliculadesc;
    export let peliculavideo;
    console.log(peliculadesc)

</script>
<style>
    .contenedor {
        max-width: 80%;

    }
    .img-fondo{
        border-radius: 2rem;
    }
    .descripcion-pelicula {
        border-radius: 2rem;
        background: linear-gradient(to right, rgba(7.06%, 9.80%, 15.29%, 1.00) 150px, rgba(7.06%, 9.80%, 15.29%, 0.54) 100%);
        display: flex;
        justify-content: center;
    }

    .poster > img {
        max-width: 30rem;
        padding: 2rem;
    }
    .contenido{
        padding: 2rem;
    }
    .contenido>h1{
        font-size: 3rem;
        font-weight: bold;
    }
    .info >p{
        font-size: 1.4rem;
        font-weight: bold;
    }
    .descripcion >p{
        font-size: 1.8rem;
        padding-top: 1.5rem;
    }
    .trailer{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding: 5rem;
    }
    .trailer h2{
        font-size: 2.8rem;
        font-weight: bold;
    }
</style>
<svelte:head>
    <title>{peliculadesc.original_title}</title>
</svelte:head>
<div class="contenedor">

    <div class="img-fondo"
         style="background: url('https://image.tmdb.org/t/p/original{peliculadesc.backdrop_path}');background-size:cover;
  background-position: center;">
        <div class="descripcion-pelicula">
            <div class="poster">
                {#if peliculadesc.poster_path}
                    <img src="https://image.tmdb.org/t/p/original{peliculadesc.poster_path}"
                         alt="{peliculadesc.title}">
                {:else}
                    <img src="https://www.jose-aguilar.com/blog/wp-content/uploads/2014/10/Imagen-no-disponible-282x300.png"
                         alt="Imagen No Disponible">
                {/if}
            </div>
            <div class="contenido">
                <h1>{peliculadesc.title}</h1>
                <div class="info">
                    <p class="estreno">
                        {peliculadesc.status}, Fecha de Estreno: {peliculadesc.release_date}
                    </p>
                    <p class="genero">
                        Generos:
                        {#each peliculadesc.genres as generos}
                            {generos.name},
                        {/each}
                    </p>
                    <p class="lenguajes">
                        Lenguaje Original:
                        {#each peliculadesc.spoken_languages as lenguaje}
                            {lenguaje.english_name}
                        {/each}
                    </p>
                </div>
                <div class="descripcion"><p>{peliculadesc.overview}</p></div>

            </div>
        </div>
    </div>
    <div class="trailer">
        <h2>Trailer </h2>
        {#if peliculavideo.results.length > 0}
            <iframe width="800" height="560" src="https://www.youtube.com/embed/{peliculavideo.results[0].key}"
                    title="YouTube video player" frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen></iframe>
        {:else}
            <p>No se encuentra ningun trailer</p>
        {/if}
    </div>
</div>