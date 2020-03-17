<template>
  <div class="card">
    <div class="card-header">{{ name }}</div>
    <div class="card-content card-content-padding">{{ cases }}</div>
  </div>
</template>
<script>
export default {
  props: ["name", "cases"]
};
</script>
<style scoped>
.card-content {
  font-size: 30px;
  font-weight: 600;
}
.card {
}
</style>