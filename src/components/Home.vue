<template>
  <div class="jumbotron">
    <h1>Trade or view your portfolio</h1>
    <h6>You may Save and Load your data </h6>
    <h6>click on 'End Day' to begin new day</h6>
    <hr>
    <p>Your Funds: {{funds | currency}}</p>
  </div>
</template>

<script>
  export default {
      computed:{
          funds(){
              return this.$store.getters.funds;
          }
      }
  }
</script>
