<template>
  <div id="app">
    <RankingTable :participants="participants"></RankingTable>
  </div>
</template>

<script>
import RankingTable from './components/RankingTable.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    RankingTable
  },
  data(){
    return {
      participants: [
        {
          'summonerName': 'NattyNatt',
          'goal': '',
          'accountInfo': {},
          'rankInfo': {}
        },
        {
          'summonerName': 'SuportChoco',
          'goal': '',
          'accountInfo': {},
          'rankInfo': {}
        },
        {
          'summonerName': 'Yuuri Leo',
          'goal': '',
          'accountInfo': {},
          'rankInfo': {}
        },
      ],
      apiKey: 'RGAPI-e4c78d6c-9b47-4a6a-b82d-26e5de87a5d2'
    };
  },

  mounted() {
    this.participants.map(p => {
      axios.get('https://euw1.api.riotgames.com/lol/summoner/v4/summoners/by-name/'+p.summonerName+'?api_key='+this.apiKey)
        .then(response => {
          // Manejar la respuesta de la API
          console.log(response.data);
          p.accountInfo = response.data;
          let url = 'https://euw1.api.riotgames.com/lol/league/v4/entries/by-summoner/'+p.accountInfo.id+'?api_key='+this.apiKey;
          axios.get(url)
            .then(response2 => {
              p.rankInfo = response2.data;
              console.log(response2.data);
            })
            .catch(error => {
              // Manejar errores
              console.error(error);
            });
        })
        .catch(error => {
          // Manejar errores
          console.error(error);
        });
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
