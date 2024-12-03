<script setup lang="ts">
import axios from 'axios';
import CardDisplay from '@/components/CardDisplay.vue';
import { ref } from 'vue';
import api from '@/assets/api';

// function pairSuccessive(arr:Array<string>) {
//     const pairs = [];
//     for (let i = 0; i < arr.length - 1; i+=2) {
//         pairs.push(`${arr[i]} + ${arr[i + 1]}`);
//     }
//     return pairs;
// }

const players = ref([
  {
    name:"Loading...",
    club: "Loading...",
    direction: "Loading...",
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
  {
    name:"Loading",
    club: "Loading",
    direction: "Loading",
    poule: "Groupe A"
  },
])

const groups = ref([
  "Groupe A",
  "Groupe A",
  "Groupe A",
  "Groupe A",
  "Groupe A",
  "Groupe A",
  "Groupe A",
  "Groupe A",
]);

const top_poules = ref([
{
    name:"Loading...",
    club: "Loading...",
    direction: "Loading...",
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
  {
    name:"Loading",
    club: "Loading",
    direction: "Loading",
    poule: "Groupe A"
  },
])

// const groups8 = computed(() => {
//   const result = pairSuccessive(groups.value)
//   return result;
// })

await axios.get( api + '/players')
.then((data) => players.value = data.data.data);

await axios.get( api + '/groups')
.then((data) => groups.value = data.data.data);

await axios.get( api + '/top-poules')
.then((data) => top_poules.value = data.data.data);



</script>

<template>
  <main class="home-view">
    <CardDisplay
    :level="16"
    :players="players"
    :groups="groups"
    />
    <!-- <CardDisplay
    :level="8"
    :players="top_poules"
    :groups="groups8"
     /> -->
    <h1>8ème de finale</h1>
    <div class="card-4" name="8eme">
      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs A & B</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
          <hr>
          <h5>Deuxième Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs C & D</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
          <hr>
          <h5>Deuxième Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs E & F</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
          <hr>
          <h5>Deuxième Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs G & H</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
          <hr>
          <h5>Deuxième Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

    </div>
    <h1>Quart de finale</h1>
    <div class="card-4" name="Quart">
      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs A & B</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs C & D</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs E & F</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs G & H</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

    </div>
    <h1>Demi-finale</h1>
    <div class="card-2" name="Demi">
      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs A & B</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>

      <div class="sub-card">
        <div class="title-box">
          <h4>Vainqueurs C & D</h4>
        </div>
        <ul>
          <li>?</li>
          <li>?</li>
          <li>?</li>
          <li>?</li>
        </ul>
        <div class="match-box">
          <h5>Premier Match</h5>
          <div class="matches">
          <p>
            ? 0 - 0 ?
          </p>
          </div>
        </div>
      </div>
    </div>
    <h1>Finale</h1>
    <div class="card-1" name="Final">
      <div class="sub-final">
        <h3>?</h3>
        <h4>0</h4>
      </div>
      <div class="centered">
      <img src="@/assets/trophee.png" />
      </div>
      <div class="sub-final">
        <h4>0</h4>
        <h3>?</h3>
      </div>
    </div>

    <div id="team-list">
      <table class="performance-table">
        <thead>
          <tr>
          <th>Nom</th>
          <th>Club</th>
          <th>Direction</th>
          <th>Poule</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="player in players" :key="player.name">
            <td> {{player.name}} </td>
            <td> {{player.club}} </td>
            <td> {{player.direction}} </td>
            <td> {{player.poule}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </main>
</template>

<style scoped>
.home-view {
  width: 100%;
  overflow: hidden;
}
.performance-table {
  width: 94%;
  border-collapse: collapse;
  font-family: Arial, sans-serif;
  margin: 0 3%;
  border-radius: 1rem;
  border: none;
  overflow: hidden;
  box-shadow: var(--secondary) 1px 1px 2px 1px;
}
.performance-table th,
.performance-table td {
  /* border: 1px solid #000; */
  padding: 8px;
  text-align: center;
}
.performance-table th {
  background-color: var(--secondary); /* Light green */
  /* font-weight: bold; */
}
.performance-table {
  text-align: left;
  background-color: white !important;
  color: black !important;
}
.card {
  display: grid;
  grid-template-columns: 12.5% 12.5% 12.5% 12.5% 12.5% 12.5% 12.5% 12.5% ;
  margin: 1% 3%;
}
.card-4 {
  display: grid;
  grid-template-columns: 25% 25% 25% 25% ;
  margin: 1% 3%;
}
.card-2 {
  display: grid;
  grid-template-columns: 50% 50%;
  margin: 1% 3%;
}
.card-1 {
  display: grid;
  grid-template-columns: 45% 10% 45%;
  /* grid-template-columns: 100%; */
  margin: 1% 3%;
  background-position: center;
  background-repeat: no-repeat;
}
.sub-card {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  overflow: hidden;
  border: var(--secondary) 1px solid;
  border-radius: 1rem;
  margin: 1rem;
  background-color: white;
  box-shadow: var(--secondary) 1px 1px 2px 1px;
}
.sub-final {
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  border: var(--secondary) 1px solid;
  border-radius: 1rem;
  margin: 1rem;
  background-color: white;
  box-shadow: var(--secondary) 1px 1px 2px 1px;
  gap: 15%;
}
.centered {
  display: flex;
  align-items: center;
  justify-content: center ;
}
ul {
  list-style-type: none;
  padding: 0;
}
.title-box {
  background-color: var(--secondary);
  width: 100%;
  text-align: center;
}
.match-box {
  background-color: var(--tertiary);
  width: 100%;
  text-align: center;
}
img {
  width: 100%;
}
</style>
