<script lang="ts">
  import MobCard from "./components/MobCard.svelte";
  import adjectives from "./data/adjectives.json";
  import animals from "./data/animals.json";

  let mobs = [
    {
      name:
        adjectives[Math.floor(Math.random() * adjectives.length)] +
        " " +
        animals[Math.floor(Math.random() * animals.length)],
      power: Math.floor(Math.random() * 20) + 1,
      health: Math.floor(Math.random() * 100) + 1,
    },
    {
      name:
        adjectives[Math.floor(Math.random() * adjectives.length)] +
        " " +
        animals[Math.floor(Math.random() * animals.length)],
      power: Math.floor(Math.random() * 20) + 1,
      health: Math.floor(Math.random() * 100) + 1,
    },
    {
      name:
        adjectives[Math.floor(Math.random() * adjectives.length)] +
        " " +
        animals[Math.floor(Math.random() * animals.length)],
      power: Math.floor(Math.random() * 20) + 1,
      health: Math.floor(Math.random() * 100) + 1,
    },
  ];
</script>

<main>
  <h1>Welcome to Auto Battler!</h1>
  <br />
  {#each mobs as mob}
    <MobCard name={mob.name} power={mob.power} health={mob.health} />
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
