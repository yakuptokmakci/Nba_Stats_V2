<template>
  <v-app>
    <v-main>
      <v-row no-gutters>
        <v-col cols="10">
          <v-sheet class="pa-2 ma-2">
            <Header></Header>
          </v-sheet>
        </v-col>
        <v-col>
          <v-sheet class="pa-2 ma-2">
            <v-btn @click="toggleTheme">change theme</v-btn>
          </v-sheet>
        </v-col>
      </v-row>
      <v-container class="spacing-playground pa-6">
        <ContentTable :players="players"></ContentTable>
        <v-row class="pa-4">
          <Compare :players="players" />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { useTheme } from "vuetify";
import axios from "axios";
import { ref, onMounted } from "vue";

const theme = useTheme();
const players = ref([]);

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? "light" : "dark";
}

onMounted(async () => {
  try {
    const response = await axios.get("src/assets/player_stats.json");
    players.value = response.data;
    console.log(response.data);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
});
</script>
