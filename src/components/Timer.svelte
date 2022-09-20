<script>
    import { onMount, onDestroy } from 'svelte';

    let initialTime
    let handle
    let duration = 60
    let elapsed = 0

    const tick = () => {
        elapsed = (new Date().getTime() - initialTime) / 1000
        if (elapsed > duration) {
            initialTime = new Date().getTime() - duration * 1000
        }
    }

    const reset = () => { initialTime = new Date().getTime() }

    onMount(() => { reset(); handle = setInterval(tick, 100) });
    onDestroy(() => clearInterval(handle))
</script>

<h2>4: Timer</h2>

<div>
    <progress value={elapsed} max={duration} /><br/>
    {elapsed.toFixed(2)}s<br/>
    Duration: <input type="range" bind:value={duration} min="10" max="100"/>{duration}s<br/>
    <button on:click={reset}>Reset</button>
</div>

<style>
    div { text-align: left; }
</style>
