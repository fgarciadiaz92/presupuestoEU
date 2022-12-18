<script>
import {listadoCanales} from "./datos.js";

let listadoCanal=null
function cambiarEstado(estado){
    const toastTrigger = document.getElementById('liveToastBtn')
    const toastLiveExample = document.getElementById('liveToast')
    if (toastTrigger) {
        toastTrigger.addEventListener('click', () => {
            const toast = new bootstrap.Toast(toastLiveExample)

            toast.show()
        })
    }
    console.log(estado)
}
</script>
<main>

    <div class="container">

    <table class="table">
        <thead>
        <tr>
            <th scope="col">Canal</th>
            <th scope="col">Estado</th>
            <th scope="col">Acciones</th>
        </tr>
        </thead>
        <tbody>
        {#each listadoCanales as canal}
            <tr>
                <td>
                    {canal.name}
                </td>
                <td>
                    {#if canal.estado}
                        <span class="badge rounded-pill text-bg-success">Activo</span>
                        {:else }
                        <span class="badge rounded-pill text-bg-danger">Inactivo</span>
                        {/if}

                </td>
                <td>
                    <button type="button" class="btn btn-outline-primary" on:click={cambiarEstado} id="liveToastBtn">Estado</button>
                    <button type="button" class="btn btn-outline-danger">Eliminar</button>


                </td>
            </tr>

            {/each}
        </tbody>
    </table>
        <div class="toast-container position-fixed bottom-0 end-0 p-3">
            <div id="liveToast" class="toast" role="alert" aria-live="assertive" aria-atomic="true">
                <div class="toast-header">
                    <strong class="me-auto">Actualizado</strong>
                    <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
                </div>
                <div class="toast-body">
                    Actualizado Correctamente
                </div>

            </div>
    </div>
</main>
<style>

</style>