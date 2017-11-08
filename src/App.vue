<template>
<div>
<nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="container">
      <div class="navbar-brand">
        <a class="navbar-item" href="https://bulma.io">
          <img src="https://upload.wikimedia.org/wikipedia/commons/7/76/Slack_Icon.png" alt="Karma++ Slak app" width="28" height="28"> 
          <strong>&nbsp &nbsp Karma++ Dashboard</strong>
        </a>
        </div>
        </div>
    </nav>
  <div class="container">
    <div>
      <router-view/>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>
  /* body { 
    background-color: #ddd
  } */
  .navbar {
    margin-bottom:20px;
  }
</style>
