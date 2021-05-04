<script>
    import {createEventDispatcher} from 'svelte'

    const dispatch = createEventDispatcher()

    function alertaprueba(event) {
        dispatch('enter', {
            text: 'prueba',
            codekey: event.keyCode
        })
    }

    export let value
</script>
<style>
    input {
        font-size: 2.2rem;
        width: 50rem;
        background: none;
        border-right: none;
        border-left: none;
        border-top: none;
        border-bottom: 0.3rem solid white;
        text-align: center;
        color: white;
    }
</style>
<input type="text" bind:value on:keypress={alertaprueba} placeholder="Buscar Pelicula">