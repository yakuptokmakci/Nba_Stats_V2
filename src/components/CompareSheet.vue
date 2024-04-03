<template>
  <v-expansion-panels>
    <v-expansion-panel title="Selected Players">
      <template #default>
        <p v-if="selectedPlayers && selectedPlayers.length > 0">
          <span v-for="(player, index) in selectedPlayers" :key="index">
            {{ player }}
            <br />
          </span>
        </p>
        <p v-else>No players selected</p>
      </template>
    </v-expansion-panel>
  </v-expansion-panels>
</template>
<script setup>
import { ref, watch, onMounted } from "vue";
import axios from "axios";

const props = defineProps({
  selectedPlayers: {
    type: Array,
    default: () => [],
  },
});

let player1Data = null;
let player2Data = null;

onMounted(async () => {
  try {
    const response = await axios.get("src/assets/player_stats.json");
    const allPlayers = response.data;
    // here i try to filter the players
    props.selectedPlayers.forEach((selectedPlayer) => {
      const filteredPlayer = allPlayers.find(
        (player) => player.Player && player.Player.includes(selectedPlayer)
      );
      if (filteredPlayer) {
        if (player1Data == null) {
          player1Data = filteredPlayer;
        } else if (player2Data == null) {
          player2Data = filteredPlayer;
        }
      }
    });

    console.log("Player 1 Data:", player1Data);
    console.log("Player 2 Data:", player2Data);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
});
</script>
