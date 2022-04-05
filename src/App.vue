<template>
  <div>
    <ul>
      <p>{{ country.population }}</p>
      <p v-if="country.world_share">{{ country.world_share.toFixed(3) }}</p>

      <div v-for="country in countries" :key="country.name">
        {{ country.name }}
        <span v-if="country.food">Food: {{ country.food }}</span>
      </div>

      <form @submit.prevent="submit">
        <label>Zoek Land</label>
        <input class="search" type="text" v-model="search" />
        <button type="submit" class="search--button">Search</button>
      </form>
    </ul>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      country: {},
      search: "",
    };
  },
  created() {
    // this.submit();
  },
  methods: {
    submit() {
      this.fetchData(`${this.search}`);
    },
    fetchData(country = "Germany") {
      this.error = this.post = null;
      this.loading = true;
      let options = {
        method: "GET",
        url: `https://world-population.p.rapidapi.com/population?country_name=${country}`,
        headers: {
          "X-RapidAPI-Host": "world-population.p.rapidapi.com",
          "X-RapidAPI-Key":
            "f9c5cf06a3msh7a64081be520eb8p1895d5jsnf31287ba1e80",
        },
      };

      axios
        .request(options)
        .then((response) => {
          console.log(response);
          this.country = response.data.body;
        })
        .catch(function (error) {
          console.error(error);
        });
    },
  },
};
// methods: {
//     getData() {
//       const options = {
//         method: "GET",
//         url: "https://world-population.p.rapidapi.com/population?country_name=Germany",
//         headers: {
//           "X-RapidAPI-Host": "world-population.p.rapidapi.com",
//           "X-RapidAPI-Key":
//             "f9c5cf06a3msh7a64081be520eb8p1895d5jsnf31287ba1e80",
//         },
//       };

//       axios
//         .request(options)
//         .then((response) => {
//           console.log(response);
//           this.country = response.data.body;
//         })
//         .catch(function (error) {
//           console.error(error);
//         });
//     },
//   },
//   created() {
//     this.getData();
//   },
// };
</script>
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
