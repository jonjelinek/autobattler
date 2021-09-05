<script lang="ts">
  // import MobCard from "./components/MobCard.svelte";
  // import { dndzone } from "svelte-dnd-action";
  import adjectives from "./data/adjectives.json";
  import animals from "./data/animals.json";
  import Board from "./Board.svelte";
  // import timer from "./timer.js";
  // const clock = timer({ interval: 500 });

  let creatureIndex = 1;

  const getMob = (index: number) => {
    return {
      id: index,
      name:
        adjectives[Math.floor(Math.random() * adjectives.length)] +
        " " +
        animals[Math.floor(Math.random() * animals.length)],
      power: Math.floor(Math.random() * 20) + 1,
      health: Math.floor(Math.random() * 100) + 1,
      level: 1,
    };
  };

  let state = "inMarket";

  let board = [
    {
      id: 1,
      name: "Player Creatures",
      items: [],
    },
    {
      id: 2,
      name: "Available Creatures",
      items: [
        getMob(creatureIndex++),
        getMob(creatureIndex++),
        getMob(creatureIndex++),
        getMob(creatureIndex++),
      ],
    },
  ];

  const refreshMobs = () => {
    state = "inMarket";
    board[1] = {
      id: 2,
      name: "Available Creatures",
      items: [
        getMob(creatureIndex++),
        getMob(creatureIndex++),
        getMob(creatureIndex++),
        getMob(creatureIndex++),
      ],
    };
    board.splice(2, 1);
  };

  const enterBattle = () => {
    board = [
      board[0],
      {
        id: 2,
        name: "Market Closed",
        items: [],
      },
      {
        id: 3,
        name: "Enemy Creatures",
        items: [
          getMob(creatureIndex++),
          getMob(creatureIndex++),
          getMob(creatureIndex++),
        ],
      },
    ];
    state = "battle";
  };

  const levelUpPlayerMobs = () => {
    if (board[0].items.length > 0) {
      board[0].items.forEach((item) => {
        item.health += 5;
        item.power += 5;
        item.level++;
      });
    }
  };

  const performAttacks = () => {
    if (board[0].items.length > 0 && board[2].items.length > 0) {
      console.log(
        board[0].items[0].name +
          " hits " +
          board[2].items[0].name +
          " for " +
          board[0].items[0].power +
          " damage!"
      );
      board[2].items[0].health -= board[0].items[0].power;
      console.log(
        board[2].items[0].name +
          " hits " +
          board[0].items[0].name +
          " for " +
          board[2].items[0].power +
          " damage!"
      );
      board[0].items[0].health -= board[2].items[0].power;
      if (board[0].items[0].health < 1) board[0].items.splice(0, 1);
      if (board[2].items[0].health < 1) board[2].items.splice(0, 1);
    } else {
      levelUpPlayerMobs();
      refreshMobs();
    }
  };

  const tick = () => {
    if (state === "battle") {
      performAttacks();
    }
  };
  setInterval(tick, 1000);
</script>

<main>
  <h1>Welcome to Auto Battler!</h1>
  <div on:click={refreshMobs}><button>Refresh Market</button></div>
  <div on:click={enterBattle}><button>Battle!</button></div>
  <Board columnItems={board} />
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
