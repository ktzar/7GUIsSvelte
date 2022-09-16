<script>
  let celsius = 0
  let fahrenheit = 0

  const calculateF = () => {
    fahrenheit = (celsius * 9/5 + 32).toFixed(2)
  }

  const calculateC = () => {
    celsius = ((fahrenheit - 32) * 5/9).toFixed(2)
  }

  calculateF()

</script>
<h2>2: Temperature converter</h2>

<input on:keyup={calculateF} bind:value={celsius} /> Celsius =
<input on:keyup={calculateC} bind:value={fahrenheit}/> Fahrenheit
