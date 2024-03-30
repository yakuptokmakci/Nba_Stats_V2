<template>
  <v-data-table
    :items="players"
    :items-per-page="7"
    class="elevation-1"
  ></v-data-table>
</template>

<script setup>
const props = defineProps(["players"]);
</script>

<style>
.v-data-table tbody tr:hover {
  cursor: pointer;
}
</style>
