<script setup lang="ts">
import api from '@/assets/api';
import axios from 'axios';
import { computed, ref } from 'vue';

const props = defineProps({
  players: {
    type: Array<{name:string, club:string, direction:string, poule:string}>,
    required: true
  },
  groups: {
    type: Array<string>,
    required: true
  },
  level: {
    type: Number,
    required: true
  }
});

const allMatches = ref([
  {
    "_id": "674eecea231a76ddd21924b7",
    "idplayer1": "674d1792d7b1f58bbd39007a",
    "idplayer2": "674d1792d7b1f58bbd39007b",
    "player1": "Player 1",
    "player2": "Player 2",
    "score1": 0,
    "score2": 0,
    "group": "Groupe A"
  }
]);

await axios.get(api + '/matches')
.then((data) => allMatches.value = data.data.data);


const matches = (current_group:string) => {
  if(props.level == 16) {
    const this_group = poule(current_group);
    return [
      `${this_group[0].player1} ${this_group[0].score1} - ${this_group[0].score2} ${this_group[0].player2}`,
      `${this_group[1].player1} ${this_group[1].score1} - ${this_group[1].score2} ${this_group[1].player2}`,
      `${this_group[2].player1} ${this_group[2].score1} - ${this_group[2].score2} ${this_group[2].player2}`,
      `${this_group[3].player1} ${this_group[3].score1} - ${this_group[3].score2} ${this_group[3].player2}`,
      `${this_group[4].player1} ${this_group[4].score1} - ${this_group[4].score2} ${this_group[4].player2}`,
      `${this_group[5].player1} ${this_group[5].score1} - ${this_group[5].score2} ${this_group[5].player2}`,
    ]
  } else if(props.level == 8) {
    const this_group = poule(current_group);
    return [
      `${this_group[0].player1} 1 - 0 ${this_group[1].player1}`,
      `${this_group[2].player1} 0 - 0 ${this_group[3].player1}`,
    ]
  }
  return 0;
};


const poule = (poule_name:string) => {
  const result = allMatches.value.filter((match) => match.group == poule_name)
  // console.log("All Group Matches for " + poule_name)
  // console.log(result)
  return result;
};
// const small_group = (groups_name) => {
//   const result = poule_players(group)
// }
const poule_players = (poule_name:string) => {
  const groups = poule_name.split(" + ")
  if( groups.length == 1){
    return props.players.filter((this_player) => this_player.poule == poule_name)
  } else {
    return props.players.filter((this_player) => this_player.poule in groups)
  }
}

const title = computed(() => {
  let result;
  switch(props.level) {
    case 16:
      result = "Matchs de Poule";
      break;
    case 8:
      result ="8ème de finale";
      break;
    default:
      result = "Error: Level not stated";
      break;

  };
  return result;
})
</script>
<template>
  <h1>{{ title }}</h1>
  <div class="my-box">
  <div class="card">
    <div class="sub-card" v-for="group in groups" :key="group">
      <div class="title-box">
        <h4>{{ group }}</h4>
      </div>
      <ul>
        <li v-for="player in poule_players(group)" :key="player.name"> {{ player.name }}</li>
      </ul>
      <div class="match-box">
        <div class="matches">
          <p v-for="match in matches(group)" :key="match">
            {{ match }}
          </p>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<style scoped>
.my-box {
  overflow-x: scroll;
}
.card {
  display: grid;
  grid-template-columns: 25% 25% 25% 25%;
  margin: 1% 3%;
  width: 200%;
}
.match-box {
  background-color: var(--tertiary);
  width: 100%;
  text-align: center;
}
.sub-card {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  overflow: hidden;
  border: var(--secondary) 1px solid;
  border-radius: 1rem;
  margin: 0.5rem;
  background-color: white;
  box-shadow: var(--secondary) 1px 1px 2px 1px;
}
.title-box {
  background-color: var(--secondary);
  width: 100%;
  text-align: center;
}
ul {
  list-style-type: none;
  padding: 0;
}
</style>
