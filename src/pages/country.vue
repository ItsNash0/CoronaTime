<template>
  <f7-page name="Country">
    <f7-navbar :title="Back" back-link="Back"></f7-navbar>
    <f7-block-title>{{foo.country}}</f7-block-title>
    <div class="card">
      <div class="card-content card-content-padding"> Total Cases: {{foo.cases}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Total Deaths: {{foo.deaths}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Today Cases: {{foo.todayCases}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Today Deaths: {{foo.todayDeaths}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Total Recovered: {{foo.recovered}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Critical Patients: {{foo.critical}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Cases per Million Inhabitants: {{foo.casesPerMillionPopulation}}</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Mortality Rate (Deaths/Cases) <br/>  {{Math.round(10000*foo.deaths/foo.cases)/100}}%</div>
    </div>
    <div class="card">
      <div class="card-content card-content-padding"> Recovery Rate (Recoverys/Cases) <br/>  {{Math.round(10000*foo.recovered/foo.cases)/100}}%</div>
    </div>
    
  </f7-page>
  
</template>
<script>
export default {
  props: ['foo'],
}
</script>

<style scoped>
.card-content {
  font-size: 18px;
  font-weight: 600;
}
</style>
