<script lang="ts">
  export let name: string, power: number, health: number, level: number;
</script>

<div class="mob">
  <h2 class="name">{name}</h2>
  <h3 class="level">Level: {level}</h3>
  Attack Power
  <div class="power" style="--power-value: {power * 10}px">{power}</div>
  Health Points
  <div class="health" style="--health-value: {health}px">{health}</div>
</div>

<style>
  .mob {
    background-color: burlywood;
    border-color: black;
    border-radius: 1px;
    border-style: dotted;
    border-width: 0.2em;
    width: 200px;
    text-align: center;
    padding: 0.5em;
    max-width: 240px;
    margin: 1em auto;
  }

  .name {
    font-weight: bold;
    padding-bottom: 1em;
  }

  .level {
    font-weight: bold;
    padding-bottom: 1em;
  }

  .power {
    background-color: cadetblue;
    width: var(--power-value);
    color: white;
  }

  .health {
    background-color: crimson;
    width: var(--health-value);
    color: white;
  }
</style>
