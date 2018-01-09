<template>
  <nav class="navbar navbar-default">
    <div class="container-fluid">
      <!-- Brand and toggle get grouped for better mobile display -->
      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <router-link class="navbar-brand" to="/">Stock Trader</router-link>
      </div>

      <!-- Collect the nav links, forms, and other content for toggling -->
      <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
        <ul class="nav navbar-nav">
          <router-link activeClass="active" to="/portfolio" tag="li" class="nav-item">
            <a class="nav-link">Portfolio</a>
          </router-link>
          <router-link activeClass="active" to="/stocks" tag="li" class="nav-item">
            <a class="nav-link">Stocks</a>
          </router-link>
        </ul>
        <strong class="navbar-text navbar-right">Funds: {{funds | currency}}</strong>
        <ul class="nav navbar-nav navbar-right">
          <li class="nav-item">
            <a @click="endDay" class="nav-link">End Day</a>
          </li>
          <li class="dropdown nav-item" :class="{open: isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
            <a
              class="dropdown-toggle nav-link" data-toggle="dropdown"
               role="button" aria-haspopup="true"
               aria-expanded="false"
               >Save & Load <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Save Data</a></li>
              <li><a href="#">Load Data</a></li>
            </ul>
          </li>
        </ul>
      </div><!-- /.navbar-collapse -->
    </div><!-- /.container-fluid -->
  </nav>
</template>

<script>
  import {mapActions} from 'vuex';
  export default {
    data(){
      return{
          isDropdownOpen: false
      }
    },
    computed:{
      funds(){
        return this.$store.getters.funds;
      }
    },
    methods:{
        ...mapActions([
            'randomizeStocks'
        ]),
        endDay(){
            this.randomizeStocks();
        }
    }
  }
</script>
