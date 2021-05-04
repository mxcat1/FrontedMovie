<script>
    import logo from '../img/logo1.png'

    export let segment;
</script>

<style>
    nav {
        border-bottom: 1px solid rgba(255, 62, 0, 0.1);
        font-weight: 300;
        padding: 0 1em;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    ul {
        margin: 0;
        padding: 0;
    }

    /* clearfix */
    ul::after {
        content: '';
        display: block;
        clear: both;
    }

    li {
        display: block;
        float: left;
    }

    [aria-current] {
        position: relative;
        display: inline-block;
    }

    [aria-current]::after {
        position: absolute;
        content: '';
        width: calc(100% - 1em);
        height: 2px;
        background-color: rgb(255, 62, 0);
        display: block;
        bottom: -1px;
    }

    a {
        text-decoration: none;
        padding: 1em 0.5em;
        display: block;
        font-size: 2rem;
        font-weight: bold;
    }

    .logo {
        display: flex;
        align-items: center;
    }

    .logo > img {
        width: 80px;
    }

    .logo > p {
        padding: 0;
        margin: 0;
        font-size: 2rem;
        font-weight: bold;
    }
</style>

<nav>
    <a class="logo" href=".">
        <img src="{logo}" alt="Logo the Movie">
        <p>MovieView</p>
    </a>
    <ul>
        <li><a aria-current="{segment === undefined ? 'page' : undefined}" href=".">Inicio</a></li>
        <li><a aria-current="{segment === 'peliculas' ? 'page' : undefined}" href="peliculas">Peliculas</a></li>

        <!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
             the blog data when we hover over the link or tap it on a touchscreen -->
<!--        <li><a rel=prefetch aria-current="{segment === 'blog' ? 'page' : undefined}" href="blog">Nosotros</a></li>-->
    </ul>
</nav>
