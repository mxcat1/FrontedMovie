<script>
    export let imgPelicula, idPelicula = null, altPelicula, tituloPelicula, descripcionPelicula = null
</script>

<style>
    div {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 3rem;
    }

    img {
        max-width: 25rem;
        border-radius: 0.5rem;
    }

    figure {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    figcaption {
        text-align: center;
        font-size: 2.2rem;
        font-weight: bold;
    }

    a {
        max-width: 26rem;
        text-align: center;
        font-size: 2.2rem;
        font-weight: bold;
    }

    .descripcion {
        text-align: center;
        max-width: 40rem;
        padding: 0.8rem;
    }

    .descripcion > p {
        text-align: justify;
        font-size: 1.6rem;
    }
</style>

<div>
    <figure>
        {#if imgPelicula}
            <img src="https://image.tmdb.org/t/p/original{imgPelicula}" alt="{altPelicula}">
        {:else}
            <img src="https://www.jose-aguilar.com/blog/wp-content/uploads/2014/10/Imagen-no-disponible-282x300.png"
                 alt="Imagen No Disponible">
        {/if}

        {#if idPelicula}
            <a href="/peliculas/{idPelicula}">
                {tituloPelicula}
            </a>
        {:else}
            <figcaption>{tituloPelicula}</figcaption>
        {/if}
    </figure>
    {#if descripcionPelicula}
        <div class="descripcion">
            <p>{descripcionPelicula}</p>
        </div>
    {/if}
</div>