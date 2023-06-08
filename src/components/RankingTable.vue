/* eslint-disable */
<template>
  <div>
    <b-table
        :items="participants"
        :fields="fields"
        class="rounded border"
        hover
    >
        <template #cell(games)="row">
          {{ row.item.rankInfo.wins }} - {{ row.item.rankInfo.losses }}
        </template>
        <template #cell(hotStreak)="row">
          {{ row.item.rankInfo.hotStreak ? 'Si' : 'No' }} 
        </template>
    </b-table>
  </div>
</template>

<script>
export default {
  name: 'RankingTable',
  props: {
    participants: Array
  },
  data(){
    return {
      fields: [
        {key: 'summonerName', label: 'Summoner', sortable: true},
        {key: 'rankInfo.tier', label: 'Liga', sortable: true},
        {key: 'rankInfo.rank', label: 'LPs', sortable: true},
        {key: 'rankInfo.hotStreak', label: 'HotStreak', sortable: true},
        {key: 'games', label: 'Games', sortable: true},
      ],
    };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
