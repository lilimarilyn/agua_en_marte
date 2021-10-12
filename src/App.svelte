<script>
  import { onMount } from "svelte";

  let myTodo;
  onMount(async () => {
    const response = await fetch(
      "https://75jwlvujpd.execute-api.us-east-2.amazonaws.com/staging/expeditions/"
    );
    const todo = await response.json();
    const convert = JSON.parse(todo.body);
    myTodo = convert;
  });
</script>

<div>
  {#if myTodo}
    <h1 class="bg-success">WATER WORLD</h1>
    <div class="container text-center">
      <div class="row">
        {#each myTodo as water}
          <div
            class="card bg-transparent col-6 col-md-4 m-2"
            style="width: 18rem;"
          >
            <!--<img src="..." class="card-img-top" alt="...">-->
            <div class="card-body bg-transparent">
              <h5 class="card-title text-info">Informacion:</h5>
              <p class="card-text">Tamaño:{water.tamano}</p>
            </div>
            <ul class="list-group list-group-flush bg-transparent">
              <li class="list-group-item bg-transparent text-warning">
                CORDENADA X:{water.x}
              </li>
              <li class="list-group-item bg-transparent text-warning">
                CORDENADA Y:{water.y}
              </li>
              <li class="list-group-item bg-transparent text-warning">
                ESTADO: {water.estado}
              </li>
            </ul>
          </div>
          <br />
        {/each}
      </div>
    </div>
  {:else}
    <p>loading.....</p>
  {/if}
</div>
