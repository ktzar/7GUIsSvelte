<script>
  import Counter from './components/Counter.svelte'
  import Temperature from './components/Temperature.svelte'
  import Flight from './components/Flight.svelte'
  import Timer from './components/Timer.svelte'
  import Crud from './components/Crud.svelte'
  import Circle from './components/Circle.svelte';
  import Sheet from './components/Sheet.svelte';

  let activeApp = null
  const show = val => {activeApp = val}
</script>

<main>
  <h1>7 GUIs in Svelte</h1>

  <button on:click={() => show(1)}>One - Counter</button>
  <button on:click={() => show(2)}>Two - Temperature converter</button>
  <button on:click={() => show(3)}>Three - Flight Booker</button>
  <button on:click={() => show(4)}>Four - Timer</button>
  <button on:click={() => show(5)}>Five - CRUD</button>
  <button on:click={() => show(6)}>Six - Circle Drawer</button>
  <button on:click={() => show(7)}>Seven - Cells</button>

  <div class="card">
  {#if activeApp === 1} <Counter /> {/if}
  {#if activeApp === 2} <Temperature /> {/if}
  {#if activeApp === 3} <Flight /> {/if}
  {#if activeApp === 4} <Timer /> {/if}
  {#if activeApp === 5} <Crud /> {/if}
  {#if activeApp === 6} <Circle /> {/if}
  {#if activeApp === 7} <Sheet /> {/if}
  </div>

</main>

<style>
</style>
