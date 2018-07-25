<template>
    <div id="app" class="row text-center">
      <div class="col-md-6 offset-md-3">
        <h2>Fortvue</h2>
        <h5>Powered by Vue.js and the Fortnite Tracker Network API.</h5>
        <SearchForm v-on:formSubmit="getPlayerData"></SearchForm>
        <PlayerInfo></PlayerInfo>
      </div>
    </div>
</template>

<script>
import SearchForm from './components/SearchForm'
import PlayerInfo from './components/PlayerInfo'

export default {
  name: 'App',
  components: {
    SearchForm,
    PlayerInfo
  },
  data() {
    return {
      playerData: ''
    }
  },
  methods: {
    getPlayerData: function(playerName, platform) {
      this.$http.get('https://api.fortnitetracker.com/v1/profile/' + platform + '/' + playerName, {
        headers: {
        'TRN-Api-Key': '9004bc7c-6975-4a77-8fa8-b777574e2331'
        }
      }).then(response => {
        console.log(response.body);
        this.playerData = response.body;
      });
    }
  }
}
</script>

<style>
body {
  margin-top: 40px;
  font-family: 'Avenir';
  background: #2d2d2d;
}

@font-face {
  font-family: Avenir;
  src: url(https://www.wfonts.com/download/data/2016/06/21/avenir/AEH.ttf);
}

</style>
