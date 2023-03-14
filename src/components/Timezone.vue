<template>
  <div>
    <form @submit.prevent="getTimezone">
      <input type="text" v-model="city" placeholder="Enter a U.S. city name">
      <button>Get Timezone</button>
    </form>
    <div v-if="timezone">
      <h2>{{ timezone }}</h2>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'TimeZone',
  data() {
    return {
      city: '',
      timezone: ''
    }
  },
  methods: {
    async getTimezone() {
      try {
        const response = await axios.get(`https://api.timezonedb.com/v2.1/get-time-zone?key=2SU4Z9IFLF2U&format=json&by=zone&zone=America/${this.city}`);
        const timezoneData = response.data;
        // console.log(timezoneData);
        const datetime = timezoneData.formatted;
        this.timezone = `The current time in ${this.city} is ${datetime}`;
      } catch(error) {
        console.log(error);
      }
    }
  }
}
</script>

<style>
button {
  background-color: blue;
  color: white;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: darkblue;
}

input[type="text"] {
  padding: 10px;
  border: 2px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  margin-right: 10px;
}

h2 {
  margin-top: 20px;
  font-size: 24px;
}
</style>

