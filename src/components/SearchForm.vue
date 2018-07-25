<template>
  <div id="app">
      <form v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="playerName" placeholder="Enter an Epic Games username.">
        <select class="form-control" v-model="platform">
          <option value="psn">PS4</option>
          <option value="xbl">Xbox</option>
          <option value="pc">PC</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Search">
      </form>
  </div>
</template>

<script>

export default {
  name: 'SearchForm',
  data() {
    return {
      playerName: '',
      platform: ''
    }
  },
  created() {
    this.platform = 'psn'
  },
  methods: {
    formSubmit(event) {
      this.$emit('formSubmit', this.playerName, this.platform);
      event.preventDefault();
    }
  }
}
</script>

<style>

.form-control {
  margin-top: 30px;
}

.btn {
  margin-top: 30px;
}

</style>
