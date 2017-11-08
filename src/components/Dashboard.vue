<template>
  <!-- <div class="columns is-mobile">
    <div class="column">1</div>
    <div class="column">2</div>
    <div class="column">3</div>
    <div class="column">4</div>
  </div> -->

  <div>

  <div class="columns">
    <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Top Karma++ Users
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr v-for="user in topReceivers" :key="user.userId">
              <td><img :src="user.user.user.profile.image_32"></td>
              <td>{{user.user.user.real_name}}</td>
              <td>{{user.karma}}</td>
            </tr>
          </table>
        </div>
      </nav>
    </div>
   <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Highest Karma++ Channels
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr v-for="channel in topChannels" :key="channel.channelId">
              <td>#{{channel.channel.channel.name}}</td>
              <td>{{channel.total}}</td>
            </tr>
          </table>
        </div>
      </nav>
    </div>
    <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Top Postive Karma++ Givers
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
          </table>
        </div>
      </nav>
    </div>
    </div>
      <div class="columns">
    <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Most negative Karma++ Givers
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
            <tr><td>pic</td><td>Terry Moore</td><td>100</td></tr>
          </table>
        </div>
      </nav>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';


export default {
  name: 'Dashboard',
  data() {
    return {
      topReceivers: [],
      topChannels: [],
    };
  },
  created() {
    axios.get('http://Terrys-MBP.attlocal.net:3000/api/receivers/T3QDS4TNY')
    .then((response) => {
      this.topReceivers = response.data;
      console.log(this.topReceivers);
    })
    .catch((e) => {
      this.errors.push(e);
    });

    axios.get('http://Terrys-MBP.attlocal.net:3000/api/channels/T3QDS4TNY')
    .then((response) => {
      this.topChannels = response.data;
      console.log(this.topChannels);
    })
    .catch((e) => {
      this.errors.push(e);
    });
  },
};
</script>

<style scoped>

</style>
