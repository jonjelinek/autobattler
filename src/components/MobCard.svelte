<script lang="ts">
  export let name: string, power: number, health: number, level: number;
  import Heart from "./heart.svg";
</script>

<div class="mob">
  <h2 class="name">{name}</h2>
  <h3 class="level">Level: {level}</h3>
  Attack Power
  <div class="power" style="--power-value: {power * 10}px">{power}</div>
  <!-- <div class="health" style="--health-value: {health}px">{health}</div> -->
  <div class="heart-container">
    <!-- https://github.com/codefeathers/rollup-plugin-svelte-svg -->
    <Heart text="test" />
    <div class="health-points">{health}</div>
  </div>
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

  .heart-container {
    position: inline;
  }
  .health-points {
    position: inline-block;
  }
</style>
