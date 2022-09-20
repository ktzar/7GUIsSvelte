<script>
  let cells = new Array(20).fill().map(a => new Array(20).fill(''))
  console.table(cells)
</script>
<h2>7: SpreadSheet</h2>

<div class="container">
<div class="inner">
  <div class="row">
      <span class="columnId"></span>
    {#each cells as row, index}
      <span class="columnId">
      {String.fromCharCode('A'.charCodeAt(0) + index)}
      </span>
    {/each}
  </div>
{#each cells as row, rowIndex}
  <div class="row">
    <span class="rowId">{rowIndex + 1}</span>
  {#each row as cell}
    <input />
  {/each}
  </div>
{/each}
</div>
</div>

<style>
  .container {
    width: 600px;
    height: 600px;
    overflow: auto 
  }

  .row {
    display: flex;
  }

  .columnId, .rowId {
    width: 60px;
  }

  .inner {
    width: 999999px;
  }

  input {
    width: 60px;
    border: 1px solid #777;

  }

</style>