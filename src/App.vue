<template>
  <div>
    <ul>
      <p>{{ country.population }}</p>
      <p v-if="country.world_share">{{ country.world_share.toFixed(3) }}</p>

      <form @submit.prevent="submit">
        <div>
          <input class="search" type="text" v-model="search" />
          <button
            type="submit"
            @click="percentagePie = country.world_share.toFixed(3)"
            class="search--button"
          >
            Search
          </button>
        </div>
        <div id="pie" v-if="country.world_share">
          <!-- Eerst update hij het getal wat binnenin de Pie chart staat. Ik moet vervolgens nog een keer klikken om ook de Pie Chart te updaten -->
          {{ country.world_share.toFixed(3) }}%
        </div>
        <div>
          <iframe
            id="iFrameYoutube"
            width="560"
            height="315"
            src="https://www.youtube.com/embed/lpQN32dXt10"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
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
      search: "Germany",
      percentagePie: "0",
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
* {
  box-sizing: border-box;
  margin: auto;
  padding: auto;
}

body {
  background: #7a8fa3;
  font: 16px Arial;
}

.logo {
  width: 80px;
}

header {
  width: 100%;
  max-width: 1200px;
  margin: auto;
  height: 133px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  color: #fff;
}

/*the container must be positioned relative:*/
#searchbar,
p,
h2,
div,
input,
button {
  margin: auto;
  padding: auto;
}
.autocomplete {
  position: relative;
  display: inline-block;
}

input {
  border: 1px solid transparent;
  background-color: #f1f1f1;
  padding: 10px;
  font-size: 16px;
  /* justify-content: center; */
}

input {
  background-color: #f1f1f1;
  width: 40%;
}

button {
  margin: 30px;
  border: 1px solid transparent;
  background-color: DodgerBlue;
  color: #fff;
  cursor: pointer;
  padding: 10px;
  font-size: 16px;
}

.autocomplete-items {
  position: absolute;
  border: 1px solid #d4d4d4;
  border-bottom: none;
  border-top: none;
  z-index: 99;
  /*position the autocomplete items to be the same width as the container:*/
  top: 100%;
  left: 0;
  right: 0;
}

.autocomplete-items div {
  padding: 10px;
  cursor: pointer;
  background-color: #fff;
  border-bottom: 1px solid #d4d4d4;
}

/*when hovering an item:*/
.autocomplete-items div:hover {
  background-color: #e9e9e9;
}

/*when navigating through the items using the arrow keys:*/
.autocomplete-active {
  background-color: DodgerBlue !important;
  color: #ffffff;
}

/* Pie chart voor percentage mensen */
#pie {
  --p: v-bind(percentagePie);
  --b: 10px;
  --c: darkred;
  --w: 200px;

  width: var(--w);
  aspect-ratio: 1;
  position: relative;
  display: inline-grid;
  margin: 5px;
  place-content: center;
  font-size: 25px;
  font-weight: bold;
  font-family: sans-serif;
}
#pie:before,
#pie:after {
  content: "";
  position: absolute;
  border-radius: 50%;
}
#pie:before {
  inset: 0;
  background: radial-gradient(farthest-side, var(--c) 98%, #0000) top/var(--b)
      var(--b) no-repeat,
    conic-gradient(var(--c) calc(var(--p) * 1%), #0000 0);
  -webkit-mask: radial-gradient(
    farthest-side,
    #0000 calc(99% - var(--b)),
    #000 calc(100% - var(--b))
  );
  mask: radial-gradient(
    farthest-side,
    #0000 calc(99% - var(--b)),
    #000 calc(100% - var(--b))
  );
}
#pie:after {
  inset: calc(50% - var(--b) / 2);
  background: var(--c);
  transform: rotate(calc(var(--p) * 3.6deg))
    translateY(calc(50% - var(--w) / 2));
}
.animate {
  animation: p 3s 0.5s both;
}
.no-round:before {
  background-size: 0 0, auto;
}
.no-round:after {
  content: none;
}
@keyframes p {
  from {
    --p: 0;
  }
  too {
    --p: 100;
  }
}
</style>
