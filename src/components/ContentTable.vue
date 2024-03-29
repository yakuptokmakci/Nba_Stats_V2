<template>
  <v-data-table
    :items="players"
    :items-per-page="7"
    class="elevation-1"
  ></v-data-table>
</template>

<script setup>
const props = defineProps(["players"]);
const headers = [
  "Player",
  "Pos",
  "Age",
  "Tm",
  "G",
  "GS",
  "MP",
  "FG",
  "FGA",
  "FG%",
  "3P",
  "3PA",
  "3P%",
  "2P",
  "2PA",
  "2P%",
  "eFG%",
  "FT",
  "FTA",
  "FT%",
  "ORB",
  "DRB",
  "TRB",
  "AST",
  "STL",
  "BLK",
  "TOV",
  "PF",
  "PTS",
];
</script>

<style>
.v-data-table tbody tr:hover {
  cursor: pointer;
}
</style>
