<template>
  <f7-page name="home">
    <!-- Top Navbar -->
    <f7-navbar :sliding="false" large>
      <f7-nav-title sliding>Corona Time</f7-nav-title>
      <f7-nav-title-large sliding>Corona time</f7-nav-title-large>
    </f7-navbar>
    <div class="card">
      <div class="card-content card-content-padding"> Total Cases: {{answer.cases}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Total Deaths: {{answer.deaths}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Total Recovered: {{answer.recovered}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Total Infected Right Now: {{answer.cases-answer.recovered-answer.deaths}}</div>
    </div>
  </f7-page>
</template>

<script>
import axios from 'axios';
  export default {
    data: () => {
      return {
        answer: "",
      }
    },
    created() {
      axios.get('http://corona.xoxoni.com/all')
      .then(response => {
        // JSON responses are automatically parsed.
        this.answer = response.data

      })
      .catch(e => {
        this.errors.push(e)
      })
    },

  }
</script>

<style scoped>
.card-content {
  font-size: 18px;
  font-weight: 600;
}
</style>