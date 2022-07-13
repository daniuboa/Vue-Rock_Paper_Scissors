<script setup>
import { ref, computed, onMounted } from "vue";

const wins = ref(0);
const draws = ref(0);
const loses = ref(0);

const choice = ref(null);
const computerChoice = ref(null);
const verdict = ref(null);

const outcomes = {
  rock: {
    rock: "draw",
    paper: "loss",
    scissors: "win",
  },
  paper: {
    rock: "win",
    paper: "draw",
    scissors: "loss",
  },
  scissors: {
    rock: "loss",
    paper: "win",
    scissors: "draw",
  },
};

const play = (c) => {
  choices.value = c;

  const choices = ["rock", "paper", "scissors"];
  const random = Math.floor(Math.random() * choices.length);
  computerChoice.value = choices[random];

  const outcome = outcomes[c][computerChoice.value];

  if (outcome === "win") {
    wins.value++;
    verdict.value == "You Win!";
  } else if (outcome === "loss") {
    loss.value++;
    verdict.value == "You Lose!";
  } else {
    draws.value++;
    verdict.value == "It's a Draw!";
  }

  saveGame();
};

const saveGame = () => {
  localStorage.setItem("wins", wins.value);
  localStorage.setItem("losses", losses.value);
  localStorage.setItem("draws", draws.value);
};

const LoadGame = () => {
  wins.value = localStorage.getItem("wins");
  draws.value = localStorage.getItem("draws");
  losses.value = localStorage.getItem("losses");
};
</script>

<template>
  <h1 class="text-3xl font-bold underline">Hello world!</h1>
</template>

<style>
</style>
