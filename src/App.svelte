<script>
  import Counter from './components/Counter.svelte'
  import Temperature from './components/Temperature.svelte'
  import Flight from './components/Flight.svelte'
  import Timer from './components/Timer.svelte'
  import Crud from './components/Crud.svelte'
  import Circle from './components/Circle.svelte';
</script>
Count
<main>
  <h1>7 GUIs in Svelte</h1>

  <div class="card">
    <Counter />
  </div>

  <div class="card">
    <Temperature />
  </div>

  <div class="card">
    <Flight />
  </div>

  <div class="card">
    <Timer />
  </div>

  <div class="card">
    <Crud />
  </div>

  <div class="card">
    <Circle />
  </div>

</main>

<style>
</style>
