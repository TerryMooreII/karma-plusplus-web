<template>
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
              <td><img class="image is-48_48 is-rounded" :src="user.user.user.profile.image_48"></td>
              <td class="is-size-5">{{user.user.user.real_name}}</td>
              <td class="is-size-5 has-text-right">{{user.karma}}</td>
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
            <tr v-for="user in topPostiveGivers" :key="user.userId">
              <td><img class="image is-48_48 is-rounded" :src="user.user.user.profile.image_48"></td>
              <td class="is-size-5">{{user.user.user.real_name}}</td>
              <td class="is-size-5 has-text-right">{{user.positiveKarma}}</td>
            </tr>
          </table>
        </div>
      </nav>
    </div>

    <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Top Negative Karma++ Givers
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr v-for="user in topNegativeGivers" :key="user.userId">
              <td><img class="image is-48_48 is-rounded" :src="user.user.user.profile.image_48"></td>
              <td class="is-size-5">{{user.user.user.real_name}}</td>
              <td class="is-size-5 has-text-right">{{user.negativeKarma}}</td>
            </tr>
          </table>
        </div>
      </nav>
    </div>
   
    
    </div>
      <div class="columns">
    <div class="column">
      <nav class="panel">
        <p class="panel-heading">
          Highest Karma++ Channels
        </p>
        <div class="panel-block">
          <table class="table is-fullwidth">
            <tr>
              <th>Channel</th>
              <th class="has-text-centered">Positive</th>
              <th class="has-text-centered">Negative</th>
              <th class="has-text-centered">Total</th>
            </tr>
            <tr v-for="channel in topChannels" :key="channel.channelId">
              <td class="is-size-5">#{{channel.channel.channel.name}}</td>
              <td class="is-size-5 has-text-centered">{{channel.positiveKarma}}</td>
              <td class="is-size-5 has-text-centered">-{{channel.negativeKarma}}</td>
              <td class="is-size-5 has-text-centered">{{channel.total}}</td>
            </tr>
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
      topPostiveGivers: [],
      topNegativeGivers: [],
    };
  },
  methods: {
    query() {
      const API_URL = process.env.API_URL;
      axios.get(`${API_URL}/api/receivers/T3QDS4TNY`)
          .then((response) => {
            this.topReceivers = response.data;
          })
          .catch((e) => {
            this.errors.push(e);
          });

      axios.get(`${API_URL}/api/channels/T3QDS4TNY`)
          .then((response) => {
            this.topChannels = response.data;
          })
          .catch((e) => {
            this.errors.push(e);
          });

      axios.get(`${API_URL}/api/givers/T3QDS4TNY?orderBy=positiveKarma`)
          .then((response) => {
            this.topPostiveGivers = response.data;
          })
          .catch((e) => {
            this.errors.push(e);
          });
      axios.get(`${API_URL}/api/givers/T3QDS4TNY?orderBy=negativeKarma`)
          .then((response) => {
            this.topNegativeGivers = response.data;
          })
          .catch((e) => {
            this.errors.push(e);
          });
    }
  },
  created() {
    setInterval(() => {
      this.query();
    }, 2 * 1000 * 60);
  },
};
</script>

<style scoped>

.is-rounded {
  border-radius: 50%;
}

</style>
