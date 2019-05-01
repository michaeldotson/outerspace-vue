<template>
  <div class="home">
    <h1>Welcome to our Solar System</h1>
    <!-- Loop through Systems -->
    <div class="planets" v-for="system in systems">
      <ul>
        <li>
          <h2>System Name: {{system.name}}</h2>
          <h4>System Radius: {{system.radius}}</h4>
        </li>
      </ul>
      

      <!-- Loop through ships -->
      <div v-for="ship in system.ships">
        <ul>
          <li>
            <hr>
            <h3>Ship Name: {{ship.name}}</h3>
            <h3>Velocity: {{ship.velocity}}</h3>
            <hr>
         </li>
        </ul>
      </div>
      
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      systems: [],
      system: {},
      ships:[],
      ship: {},
    };
  },
  created: function() {
    axios.get("/api/ships").then(response => {
      console.log(response.data);
      this.ships = response.data;
    });
    axios.get("/api/systems").then(response => {
      console.log(response.data);
      this.systems = response.data;
    });
  },
  methods: {}
};
</script>