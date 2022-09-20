<script>
  let circles = []
  let active = 0
  let size = 50

  let undone

  function newCircle(evt) {
    circles = [...circles, {x: evt.offsetX, y: evt.offsetY, r: 50}]
  }

  function setActive(index) { active = index }

  function resize() { circles[active].r = size }

  function undo() {
    [undone] = circles.splice(circles.length-1, 1)
    circles = circles
  }

  function redo() {
    undone && circles.push(undone)
    circles = circles
  }

</script>
<h2>6: Circle</h2>

<div class="container">
  <div>
    <button on:click={undo}>Undo</button>
    <button on:click={redo}>Redo</button>
  </div>
  <svg on:click={newCircle} width="400" height="400">
    {#each circles as circle, index}
    <circle
      on:click|stopPropagation={() => setActive(index)}
      cx={circle.x}
      cy={circle.y}
      r={circle.r}
      fill={active === index ? '#ccc' : '#fff'}
      stroke="#333"
    />
    {/each}
  </svg>
  <br/>
  <input bind:value={size} on:change={resize} type="range" min="10" max="100"/>
</div>

<style>
  svg {
    border: 1px solid black
  }
</style>