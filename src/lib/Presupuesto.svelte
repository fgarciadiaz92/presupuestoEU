<script>
    import {listadoDatos} from "./datos.js";

    let datos=null
    let totalIndividual=null
    let total=null
    let valoresTotales=null

    function calcularRequerido(){
        totalIndividual=0
        datos=listadoDatos
        datos.forEach(function (x){
            if(x.requerido){
                totalIndividual+=parseInt(x.valorIndividual)}
            })
    }
    function reset() {
        alert("trabajando")
    }
</script>
<main>
    <div class="container">
        <table class="table">
            <thead class="table-dark" >
            <tr>
                <th scope="col">Gasto</th>
                <th scope="col">Individual</th>
                <th scope="col">Total</th>
                <th scope="col">Requerido</th>
                <th scope="col">Pagado</th>
            </tr>
            </thead>
            <tbody class="table-group-divider">
            {#each listadoDatos as data}
            <tr class:table-success={data.requerido}>
                <td>{data.name}</td>
                <td class="col col-lg-2">
                    <input type="email" class="form-control" placeholder="Ingrese un valor" bind:value={data.valorIndividual} id="inputValor" >
                </td>
                <td class="col col-lg-2">
                    <input type="email" class="form-control" disabled>
                </td>
                <td >
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" id="flexCheckDefault" bind:checked={data.requerido}>
                        <label class="form-check-label" for="flexCheckDefault">
                            {#if data.requerido}
                                Aportara
                                {:else}
                                No Aportara
                            {/if}
                        </label>
                    </div>
                </td>
                <td >
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox" bind:checked={data.pagado}>
                        <label class="form-check-label" for="flexCheckDefault">
                            {#if data.pagado}
                                Pagado
                            {:else}
                                No Pagado
                            {/if}
                        </label>
                    </div>
                </td>
            </tr>
                {/each}
            <tr>
                <td  class="col col-lg-2">
                    <button type="button" class="btn btn-primary" on:click={calcularRequerido}>Calcular</button>
                    <button type="button" class="btn btn-danger" on:click={reset}>Reset</button>
                </td>
                <td class="col col-lg-2">  <input  class="form-control" bind:value={totalIndividual} disabled></td>
                <td  class="col col-lg-2"> <input class="form-control" bind:value={total} disabled></td>
                <td  class="col col-lg-2">  </td>
                <td  class="col col-lg-2">  </td>
            </tr>
            </tbody>
        </table>
    </div>
</main>
<style>
</style>