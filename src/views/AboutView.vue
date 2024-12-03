<template>
  <div class="about" v-for="current_group in groups" :key="current_group">
    <PerformanceTable
    :table-headers="Object.keys(players[0])"
    :table-data="players.filter((player) => player.poule == current_group).flat()"
    />
  </div>
</template>

<style scoped>
.about {
  margin: 2% 3%;
}
</style>

<script setup lang="ts">
import api from '@/assets/api';
import PerformanceTable from '@/components/PerformanceTable.vue';
import axios from 'axios';
import { ref } from 'vue';
const players = ref([
  {
    name:"Loading...",
    club: "Loading...",
    direction: "Loading...",
    poule: "Groupe A",
    score: 0
  },
  {
    name:"Loading",
    club: "Loading",
    direction: "Loading",
    poule: "Groupe A"
  },
  {
    name:"Loading",
    club: "Loading",
    direction: "Loading",
    poule: "Groupe A"
  },
  {
    name:"Loading",
    club: "Loading",
    direction: "Loading",
    poule: "Groupe A"
  },
])

const groups = ref([]);

await axios.get(api + '/scores')
.then((data) => players.value = data.data.data)

await axios.get(api + '/groups')
.then((data) => groups.value = data.data.data)
</script>
