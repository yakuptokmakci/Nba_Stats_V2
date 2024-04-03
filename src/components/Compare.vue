<template>
  <v-btn block outlined elevation="6" color="secondary" @click="handleClick">
    {{ buttontext }}
  </v-btn>

  <v-autocomplete
    v-if="isCompare"
    label="Player 1"
    :items="getPlayerNames(players)"
    item-text="Player"
    variant="solo"
  ></v-autocomplete>
  <v-autocomplete
    v-if="isCompare"
    label="Player 2"
    :items="getPlayerNames(players)"
    item-text="Player"
    variant="solo"
  ></v-autocomplete>
  <v-btn
    v-if="isCompare"
    block
    outlined
    elevation="6"
    color="secondary"
    @click="compareClick"
  >
    Compare
  </v-btn>
  <CompareSheet v-if="iscompactive" />
</template>

<script setup>
import { ref } from "vue";

const isCompare = ref(false);
const buttontext = ref("Compare Players");
const props = defineProps(["players"]);
const iscompactive = ref(false);

const handleClick = () => {
  isCompare.value = !isCompare.value;
  if (!isCompare.value) {
    buttontext.value = "Compare Players";
    iscompactive.value = false;
  } else {
    buttontext.value = "End Process";
  }
  console.log(isCompare.value);
};

const compareClick = () => {
  iscompactive.value = !iscompactive.value;
};

const getPlayerNames = (players) => {
  return players.map(
    (player) => player.Player + " Pos: " + player.Pos + " Team: " + player.Tm
  );
};
</script>
