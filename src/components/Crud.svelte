<script>
  let prefix = ''
  let editing = 1
  let name
  let surname

  let records = [
    {name: 'Hans', surname: 'Emil'},
    {name: 'Max', surname: 'Mustermann'},
    {name: 'Roman', surname: 'Tisch'}
  ]

  $: filteredRecords = records.filter(
    a =>
      a.name.indexOf(prefix) === 0 ||
      a.surname.indexOf(prefix) === 0
    )

  function create() {
    records.push({name, surname})
  }

  function update() {
    console.log(records, editing, name, surname)
    records[editing] = {name, surname}
  }

  function remove() {
    records.splice(editing, 1)
  }

  function setEditing(index) {
    editing = index
    name = filteredRecords[index].name
    surname = filteredRecords[index].surname
  }

</script>
<h2>5: CRUD</h2>

<div class="container">
  <div class="row">
    <div class="column">
      Filter prefix: <input bind:value={prefix}/>
    </div>
    <div class="column"></div>
  </div>
  <div class="row">
    <div class="column">
      <ul>
        {#each filteredRecords as record, index}
          <li on:click={() => setEditing(index)} class={editing===index && 'active'}>{record.name} {record.surname}</li>
        {/each}
      </ul>
    </div>
    <div class="column">
        Name: <input bind:value={name} /><br/>
        Surname: <input bind:value={surname} />
    </div>
  </div>
  <div class="row">
    <button on:click={create}>Create</button>
    <button on:click={update}>Update</button>
    <button on:click={remove}>Delete</button>
  </div>
</div>

<style>
  .container {
    text-align: left;
  }

  ul {
    list-style: none;
    padding-left: 0;
    border: 1px solid #333;
    background: white;
  }

  li {
    cursor: pointer;
  }

  li.active {
    background: blue;
    color: white
  }

  .row {
    display: flex;
    justify-content: space-evenly;
  }
</style>