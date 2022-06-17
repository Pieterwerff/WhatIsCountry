<template>
  <!-- Startpagina -->
  <div v-if="newInstance == true">
    <!-- logo -->
    <img id="logo" src="src/assets/logo.png" alt="WhatIsCountryLogo" />
    <!-- Introductie bericht -->
    <p>
      Hey there! This website is made for people with an interest in geopraphy.
      I wanted to make a really simple and easy to use website where people can
      find all sorts of information about a country of interest!
    </p>
    <p>
      If you think you know your countries, feel free to test your knowledge! :)
    </p>
    <!-- Knop naar de app -->
    <button style="margin: 10px" @click="newInstance = false">
      Let me explore!
    </button>
  </div>
  <!-- app start als de knop let me explore world ingedrukt -->
  <div v-else>
    <!-- logo en kies een land -->
    <img id="logo" src="src/assets/logo.png" alt="WhatIsCountryLogo" />
    <h1 v-if="country.world_share"></h1>
    <h1 v-else>Choose a country!</h1>
    <!-- Selector voor alle landen -->
    <div id="selector">
      <form @submit.prevent="submit">
        <select v-model="search" id="countrySelector" name="country">
          <option value="Afghanistan">Afghanistan</option>
          <option value="Aland Islands">Aland Islands</option>
          <option value="Albania">Albania</option>
          <option value="Algeria">Algeria</option>
          <option value="American Samoa">American Samoa</option>
          <option value="Andorra">Andorra</option>
          <option value="Angola">Angola</option>
          <option value="Anguilla">Anguilla</option>
          <option value="Antarctica">Antarctica</option>
          <option value="Antigua and Barbuda">Antigua and Barbuda</option>
          <option value="Argentina">Argentina</option>
          <option value="Armenia">Armenia</option>
          <option value="Aruba">Aruba</option>
          <option value="Australia">Australia</option>
          <option value="Austria">Austria</option>
          <option value="Azerbaijan">Azerbaijan</option>
          <option value="Bahamas">Bahamas</option>
          <option value="Bahrain">Bahrain</option>
          <option value="Bangladesh">Bangladesh</option>
          <option value="Barbados">Barbados</option>
          <option value="Belarus">Belarus</option>
          <option value="Belgium">Belgium</option>
          <option value="Belize">Belize</option>
          <option value="Benin">Benin</option>
          <option value="Bermuda">Bermuda</option>
          <option value="Bhutan">Bhutan</option>
          <option value="Bolivia">Bolivia</option>
          <option value="Bonaire, Sint Eustatius and Saba">
            Bonaire, Sint Eustatius and Saba
          </option>
          <option value="Bosnia and Herzegovina">Bosnia and Herzegovina</option>
          <option value="Botswana">Botswana</option>
          <option value="Bouvet Island">Bouvet Island</option>
          <option value="Brazil">Brazil</option>
          <option value="British Indian Ocean Territory">
            British Indian Ocean Territory
          </option>
          <option value="Brunei Darussalam">Brunei Darussalam</option>
          <option value="Bulgaria">Bulgaria</option>
          <option value="Burkina Faso">Burkina Faso</option>
          <option value="Burundi">Burundi</option>
          <option value="Cambodia">Cambodia</option>
          <option value="Cameroon">Cameroon</option>
          <option value="Canada">Canada</option>
          <option value="Cape Verde">Cape Verde</option>
          <option value="Cayman Islands">Cayman Islands</option>
          <option value="Central African Republic">
            Central African Republic
          </option>
          <option value="Chad">Chad</option>
          <option value="Chile">Chile</option>
          <option value="China">China</option>
          <option value="Christmas Island">Christmas Island</option>
          <option value="Cocos (Keeling) Islands">
            Cocos (Keeling) Islands
          </option>
          <option value="Colombia">Colombia</option>
          <option value="Comoros">Comoros</option>
          <option value="Congo">Congo</option>
          <option value="Congo, Democratic Republic of the Congo">
            Congo, Democratic Republic of the Congo
          </option>
          <option value="Cook Islands">Cook Islands</option>
          <option value="Costa Rica">Costa Rica</option>
          <option value="Cote D'Ivoire">Cote D'Ivoire</option>
          <option value="Croatia">Croatia</option>
          <option value="Cuba">Cuba</option>
          <option value="Curacao">Curacao</option>
          <option value="Cyprus">Cyprus</option>
          <option value="Czech Republic">Czech Republic</option>
          <option value="Denmark">Denmark</option>
          <option value="Djibouti">Djibouti</option>
          <option value="Dominica">Dominica</option>
          <option value="Dominican Republic">Dominican Republic</option>
          <option value="Ecuador">Ecuador</option>
          <option value="Egypt">Egypt</option>
          <option value="El Salvador">El Salvador</option>
          <option value="Equatorial Guinea">Equatorial Guinea</option>
          <option value="Eritrea">Eritrea</option>
          <option value="Estonia">Estonia</option>
          <option value="Ethiopia">Ethiopia</option>
          <option value="Falkland Islands (Malvinas)">
            Falkland Islands (Malvinas)
          </option>
          <option value="Faroe Islands">Faroe Islands</option>
          <option value="Fiji">Fiji</option>
          <option value="Finland">Finland</option>
          <option value="France">France</option>
          <option value="French Guiana">French Guiana</option>
          <option value="French Polynesia">French Polynesia</option>
          <option value="French Southern Territories">
            French Southern Territories
          </option>
          <option value="Gabon">Gabon</option>
          <option value="Gambia">Gambia</option>
          <option value="Georgia">Georgia</option>
          <option value="Germany">Germany</option>
          <option value="Ghana">Ghana</option>
          <option value="Gibraltar">Gibraltar</option>
          <option value="Greece">Greece</option>
          <option value="Greenland">Greenland</option>
          <option value="Grenada">Grenada</option>
          <option value="Guadeloupe">Guadeloupe</option>
          <option value="Guam">Guam</option>
          <option value="Guatemala">Guatemala</option>
          <option value="Guernsey">Guernsey</option>
          <option value="Guinea">Guinea</option>
          <option value="Guinea-Bissau">Guinea-Bissau</option>
          <option value="Guyana">Guyana</option>
          <option value="Haiti">Haiti</option>
          <option value="Heard Island and Mcdonald Islands">
            Heard Island and Mcdonald Islands
          </option>
          <option value="Holy See (Vatican City State)">
            Holy See (Vatican City State)
          </option>
          <option value="Honduras">Honduras</option>
          <option value="Hong Kong">Hong Kong</option>
          <option value="Hungary">Hungary</option>
          <option value="Iceland">Iceland</option>
          <option value="India">India</option>
          <option value="Indonesia">Indonesia</option>
          <option value="Iran, Islamic Republic of">
            Iran, Islamic Republic of
          </option>
          <option value="Iraq">Iraq</option>
          <option value="Ireland">Ireland</option>
          <option value="Isle of Man">Isle of Man</option>
          <option value="Israel">Israel</option>
          <option value="Italy">Italy</option>
          <option value="Jamaica">Jamaica</option>
          <option value="Japan">Japan</option>
          <option value="Jersey">Jersey</option>
          <option value="Jordan">Jordan</option>
          <option value="Kazakhstan">Kazakhstan</option>
          <option value="Kenya">Kenya</option>
          <option value="Kiribati">Kiribati</option>
          <option value="Korea, Democratic People's Republic of">
            Korea, Democratic People's Republic of
          </option>
          <option value="Korea, Republic of">Korea, Republic of</option>
          <option value="Kosovo">Kosovo</option>
          <option value="Kuwait">Kuwait</option>
          <option value="Kyrgyzstan">Kyrgyzstan</option>
          <option value="Lao People's Democratic Republic">
            Lao People's Democratic Republic
          </option>
          <option value="Latvia">Latvia</option>
          <option value="Lebanon">Lebanon</option>
          <option value="Lesotho">Lesotho</option>
          <option value="Liberia">Liberia</option>
          <option value="Libyan Arab Jamahiriya">Libyan Arab Jamahiriya</option>
          <option value="Liechtenstein">Liechtenstein</option>
          <option value="Lithuania">Lithuania</option>
          <option value="Luxembourg">Luxembourg</option>
          <option value="Macao">Macao</option>
          <option value="Macedonia, the Former Yugoslav Republic of">
            Macedonia, the Former Yugoslav Republic of
          </option>
          <option value="Madagascar">Madagascar</option>
          <option value="Malawi">Malawi</option>
          <option value="Malaysia">Malaysia</option>
          <option value="Maldives">Maldives</option>
          <option value="Mali">Mali</option>
          <option value="Malta">Malta</option>
          <option value="Marshall Islands">Marshall Islands</option>
          <option value="Martinique">Martinique</option>
          <option value="Mauritania">Mauritania</option>
          <option value="Mauritius">Mauritius</option>
          <option value="Mayotte">Mayotte</option>
          <option value="Mexico">Mexico</option>
          <option value="Micronesia, Federated States of">
            Micronesia, Federated States of
          </option>
          <option value="Moldova, Republic of">Moldova, Republic of</option>
          <option value="Monaco">Monaco</option>
          <option value="Mongolia">Mongolia</option>
          <option value="Montenegro">Montenegro</option>
          <option value="Montserrat">Montserrat</option>
          <option value="Morocco">Morocco</option>
          <option value="Mozambique">Mozambique</option>
          <option value="Myanmar">Myanmar</option>
          <option value="Namibia">Namibia</option>
          <option value="Nauru">Nauru</option>
          <option value="Nepal">Nepal</option>
          <option value="Netherlands">Netherlands</option>
          <option value="Netherlands Antilles">Netherlands Antilles</option>
          <option value="New Caledonia">New Caledonia</option>
          <option value="New Zealand">New Zealand</option>
          <option value="Nicaragua">Nicaragua</option>
          <option value="Niger">Niger</option>
          <option value="Nigeria">Nigeria</option>
          <option value="Niue">Niue</option>
          <option value="Norfolk Island">Norfolk Island</option>
          <option value="Northern Mariana Islands">
            Northern Mariana Islands
          </option>
          <option value="Norway">Norway</option>
          <option value="Oman">Oman</option>
          <option value="Pakistan">Pakistan</option>
          <option value="Palau">Palau</option>
          <option value="Palestinian Territory, Occupied">
            Palestinian Territory, Occupied
          </option>
          <option value="Panama">Panama</option>
          <option value="Papua New Guinea">Papua New Guinea</option>
          <option value="Paraguay">Paraguay</option>
          <option value="Peru">Peru</option>
          <option value="Philippines">Philippines</option>
          <option value="Pitcairn">Pitcairn</option>
          <option value="Poland">Poland</option>
          <option value="Portugal">Portugal</option>
          <option value="Puerto Rico">Puerto Rico</option>
          <option value="Qatar">Qatar</option>
          <option value="Reunion">Reunion</option>
          <option value="Romania">Romania</option>
          <option value="Russian Federation">Russian Federation</option>
          <option value="Rwanda">Rwanda</option>
          <option value="Saint Barthelemy">Saint Barthelemy</option>
          <option value="Saint Helena">Saint Helena</option>
          <option value="Saint Kitts and Nevis">Saint Kitts and Nevis</option>
          <option value="Saint Lucia">Saint Lucia</option>
          <option value="Saint Martin">Saint Martin</option>
          <option value="Saint Pierre and Miquelon">
            Saint Pierre and Miquelon
          </option>
          <option value="Saint Vincent and the Grenadines">
            Saint Vincent and the Grenadines
          </option>
          <option value="Samoa">Samoa</option>
          <option value="San Marino">San Marino</option>
          <option value="Sao Tome and Principe">Sao Tome and Principe</option>
          <option value="Saudi Arabia">Saudi Arabia</option>
          <option value="Senegal">Senegal</option>
          <option value="Serbia">Serbia</option>
          <option value="Serbia and Montenegro">Serbia and Montenegro</option>
          <option value="Seychelles">Seychelles</option>
          <option value="Sierra Leone">Sierra Leone</option>
          <option value="Singapore">Singapore</option>
          <option value="Sint Maarten">Sint Maarten</option>
          <option value="Slovakia">Slovakia</option>
          <option value="Slovenia">Slovenia</option>
          <option value="Solomon Islands">Solomon Islands</option>
          <option value="Somalia">Somalia</option>
          <option value="South Africa">South Africa</option>
          <option value="South Georgia and the South Sandwich Islands">
            South Georgia and the South Sandwich Islands
          </option>
          <option value="South Sudan">South Sudan</option>
          <option value="Spain">Spain</option>
          <option value="Sri Lanka">Sri Lanka</option>
          <option value="Sudan">Sudan</option>
          <option value="Suriname">Suriname</option>
          <option value="Svalbard and Jan Mayen">Svalbard and Jan Mayen</option>
          <option value="Swaziland">Swaziland</option>
          <option value="Sweden">Sweden</option>
          <option value="Switzerland">Switzerland</option>
          <option value="Syrian Arab Republic">Syrian Arab Republic</option>
          <option value="Taiwan, Province of China">
            Taiwan, Province of China
          </option>
          <option value="Tajikistan">Tajikistan</option>
          <option value="Tanzania, United Republic of">
            Tanzania, United Republic of
          </option>
          <option value="Thailand">Thailand</option>
          <option value="Timor-Leste">Timor-Leste</option>
          <option value="Togo">Togo</option>
          <option value="Tokelau">Tokelau</option>
          <option value="Tonga">Tonga</option>
          <option value="Trinidad and Tobago">Trinidad and Tobago</option>
          <option value="Tunisia">Tunisia</option>
          <option value="Turkey">Turkey</option>
          <option value="Turkmenistan">Turkmenistan</option>
          <option value="Turks and Caicos Islands">
            Turks and Caicos Islands
          </option>
          <option value="Tuvalu">Tuvalu</option>
          <option value="Uganda">Uganda</option>
          <option value="Ukraine">Ukraine</option>
          <option value="United Arab Emirates">United Arab Emirates</option>
          <option value="United Kingdom">United Kingdom</option>
          <option value="United States">United States</option>
          <option value="United States Minor Outlying Islands">
            United States Minor Outlying Islands
          </option>
          <option value="Uruguay">Uruguay</option>
          <option value="Uzbekistan">Uzbekistan</option>
          <option value="Vanuatu">Vanuatu</option>
          <option value="Venezuela">Venezuela</option>
          <option value="Viet Nam">Viet Nam</option>
          <option value="Virgin Islands, British">
            Virgin Islands, British
          </option>
          <option value="Virgin Islands, U.s.">Virgin Islands, U.s.</option>
          <option value="Wallis and Futuna">Wallis and Futuna</option>
          <option value="Western Sahara">Western Sahara</option>
          <option value="Yemen">Yemen</option>
          <option value="Zambia">Zambia</option>
          <option value="Zimbabwe">Zimbabwe</option>
        </select>
        <button
          @click="testKnowledge = false"
          style="margin: 10px"
          type="submit"
          class="search--button"
        >
          Search
        </button>
        <button
          style="margin: 10px; background-color: darkred"
          @click="
            (testKnowledge = true),
              (guessedOne = false),
              (probablyCheated = false)
          "
        >
          Test knowledge!
        </button>
      </form>
    </div>
    <!-- als er geen land geselecteerd NA het zoeken, zal hij een foutmelding geven. Ik wilde dit eigenlijk doen door het error object op te halen uit de IPA maar dat is niet gelukt -->
    <div v-if="searched == true">
      <p v-if="errorMessage">{{ errorMessage }}</p>
    </div>
    <!-- De app doet een kleine quizz met de informatie die hij uit de 2 IPA's haalt -->
    <div v-if="testKnowledge == true">
      <div v-if="country.world_share">
        <h2>
          What do you think the total population of
          {{ country.country_name }} is?
        </h2>
        <br />
        <!-- Als de vraag onbeantwoord is, zal hij dit scherm laten zien om mensen te laten gokken -->
        <div v-if="guessedOne == false">
          <input v-model="populationGuess" @keypress="isNumber($event)" />
          <button @click="calculateAnswer(populationGuess, country.population)">
            Take Guess!
          </button>
        </div>
        <!-- Als de vraag wordt beantwoord laat hij dit zien -->
        <div v-if="guessedOne == true">
          <h2 v-if="probablyCheated == true">
            Nice, you guessed the exact population size! You probably cheated,
            didn't you ;) Your guess is:
          </h2>
          <h2 v-else>
            You're only {{ amountOff }} off! The exact amount is
            {{ country.population }}, which is
          </h2>
          <span id="pie" v-if="country.world_share">
            {{ country.world_share.toFixed(5) }}%
          </span>
          <h2 v-if="country.world_share">Of the world's population!</h2>
        </div>
      </div>
      <!-- ***** -->
      <!-- Hier wil ik nog een tweede vraag maken. namelijk, Wat is de hoofdstad van het gekozen land? Tot op heden heeft dit nog niet gewerkt helaas, daarom haal ik het uit de code -->
      <!-- ***** -->
      <!--  -->
      <!-- <div v-if="showSecond == true">
        <p>
          Next up, capital! What do you think is the capital of
          {{ weather.location.country }}?
          <input v-model="countryGuess" />
          <button @click="nameGuessAnswer(countryGuess, weather.location.name)">
            Take Guess!
          </button>
        </p>
        <p v-if="rightAnswer == true">
          Well done! You got the correct answer: {{ weather.location.name }}
        </p>
        <p v-if="wrongAnswer == true">
          Sorry, that is not the correct answer! The right answer is:
          {{ weather.location.name }}
        </p>
        <p v-if="weather.current.temp_c">
          Currently the temperature in {{ weather.location.name }} is

          {{ weather.current.temp_c }} °C
        </p>
        <p>
          The weather is {{ weather.current.condition.text }}
          <img
            :src="weather.current.condition.icon"
            style="width: 10%; margin: auto; display: block"
            alt=""
          />
        </p>
        <p>The current date and time in {{ weather.location.name }} are:</p>
        <h2>{{ weather.location.localtime }}</h2>
      </div>  -->
    </div>
    <!-- De app Laat de informatie zien over een land -->
    <div v-if="testKnowledge == false">
      <!-- Als hij informatie heeft gekregen uit de IPA zal hij deze laten zien -->
      <div v-if="country.world_share">
        <h2>
          >The population of {{ country.country_name }} is <br />
          {{ country.population }}, <br />
          which is
        </h2>
      </div>
      <!-- Hiermee heb ik een pie chart die het percentage laat zien in vergelijking tot de wereldbevolking -->
      <div id="pie" v-if="country.world_share">
        {{ country.world_share.toFixed(5) }}%
      </div>
      <div v-if="country.world_share"><h2>Of the world's population!</h2></div>
      <div v-if="country.world_share">
        <!-- Met de tweede IPA heb ik de hoofdstad, temperatuur, icoontje hiervan en datum en tijd opgehaald en laat ik hier zien-->
        <p>
          The capital of {{ weather.location.country }} is
          {{ weather.location.name }}
        </p>
        <p v-if="weather.current.temp_c">
          Currently the temperature in {{ weather.location.name }} is

          {{ weather.current.temp_c }} °C
        </p>
        <p>
          The weather is {{ weather.current.condition.text }}
          <img
            :src="weather.current.condition.icon"
            style="width: 10%; margin: auto; display: block"
            alt=""
          />
        </p>
        <p>The current date and time in {{ weather.location.name }} are:</p>
        <h2>{{ weather.location.localtime }}</h2>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      // Alle default staten van de variabelen
      country: {},
      weather: {},
      errorMessage: "",
      search: "",
      percentagePie: "0",
      searched: false,
      newInstance: true,
      testKnowledge: false,
      guessedOne: false,
      probablyCheated: false,
      // showSecond: false,
      // guessedTwo: true,
      amountOff: 0,
      // rightAnswer: false,
      // wrongAnswer: false,
    };
  },
  created() {
    // this.submit();
  },
  methods: {
    // Hiermee maakt hij de objecten leeg en vult hij ze met de nieuwe landen
    submit() {
      this.country = {};
      this.weather = {};
      this.fetchCountryData(`${this.search}`);
      this.fetchCountryWeather(`${this.search}`);
    },
    // Rekent het antwoord uit op de eerste kennisvraag
    calculateAnswer(guess, totalPopulation) {
      if (guess == totalPopulation) {
        this.probablyCheated = true;
      }
      this.amountOff = (guess - totalPopulation) * -1;
      this.guessedOne = true;
      this.guessedTwo = false;
      this.showSecond = true;
    },
    // ****
    // Deze functie is bedoeld voor de tweede vraag, omdat ik deze niet af heb kunnen maken haal ik ze uit de actieve code
    // ****
    // nameGuessAnswer(guess, name) {
    //   if (guess.toLowerCase.trim() == name.toLowerCase.trim()) {
    //     this.rightAnswer = true;
    //     console.log(guess);
    //   } else {
    //     this.wrongAnswer = true;
    //     console.log(name);
    //   }
    //   this.guessedTwo = true;
    // },

    // Voor de eerste quizvraag is het belangrijk dat er geen letters getypt worden in de textbox, dat doe ik met deze funcite
    isNumber: function (evt) {
      evt = evt ? evt : window.event;
      var charCode = evt.which ? evt.which : evt.keyCode;
      if (
        charCode > 31 &&
        (charCode < 48 || charCode > 57) &&
        charCode !== 46
      ) {
        evt.preventDefault();
      } else {
        return true;
      }
    },
    // Aantal mensen van land ophalen
    fetchCountryData(country = "") {
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
          this.errorMessage = "";
          this.country = response.data.body;
          // VAN TOM: Volgens mij kun je hier je percentagePie gewoon updaten met de data die je binnenkrijgt.
          // Omdat je percentagePie in je data hebt staan op regel 366 kun je hem hier updaten
          // en je template laat meteen de waarde zien als er wat veranderd.
          this.percentagePie = response.data.body.world_share.toFixed(7);
        })
        .catch((error) => {
          if (error.response) {
            console.log(error);
            this.errorMessage = error.response.data.message;
            // Request made and server responded
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
            console.log(error.response.data.message);
          } else if (error.request) {
            // The request was made but no response was received
            console.log(error.request);
          } else {
            // Something happened in setting up the request that triggered an Error
            console.log("Error", error.message);
          }
        });
      this.searched = true;
    },
    // De hoofdstad en het weer ophalen
    fetchCountryWeather(weatherRequest) {
      this.error = this.post = null;
      this.loading = true;
      let options = {
        method: "GET",
        url: "https://weatherapi-com.p.rapidapi.com/current.json",
        params: { q: weatherRequest },
        headers: {
          "X-RapidAPI-Key":
            "f63af4fb4bmsh88069a0b1a57525p17dfa2jsn9c74e840185b",
          "X-RapidAPI-Host": "weatherapi-com.p.rapidapi.com",
        },
      };

      axios
        .request(options)
        .then((response) => {
          console.log(response);
          this.weather = response.data;
        })
        .catch((error) => {
          if (error.response) {
            // Request made and server responded
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
            console.log(error.response.data.message);
          } else if (error.request) {
            // The request was made but no response was received
            console.log(error.request);
          } else {
            // Something happened in setting up the request that triggered an Error
            console.log("Error", error.message);
          }
        });
    },
  },
};
</script>
<style>
/* Basis stijl voor de app zelf */
#app {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #9aa6b0;
  width: 60%;
  padding: 50px;
}
* {
  box-sizing: border-box;
  margin: auto;
  padding: auto;
}
.logo {
  width: 80px;
}
body {
  background: white;
}
/* header {
  width: 100%;
  max-width: 1200px;
  margin: auto;
  height: 133px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  color: #fff;
} */

/* voor de input en zoekbalk */
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
/* opmaak voor quiz tekstbalk */
input {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border: 1px solid transparent;
  background-color: #f1f1f1;
  padding: 10px;
  font-size: 16px;
  /* justify-content: center; */
}
#countrySelector {
  margin: 15px;
  margin-right: 0px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border: 1px solid transparent;
  background-color: #f1f1f1;
  padding: 10px;
  font-size: 16px;
  /* justify-content: center; */
}
/* knop opmaak */
button {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  border: 1px solid transparent;
  background-color: DodgerBlue;
  color: #fff;
  cursor: pointer;
  padding: 10px;
  font-size: 16px;
}
/* Pie chart voor percentage mensen */
#pie {
  --p: v-bind(percentagePie);
  --b: 4px;
  --c: darkred;
  --w: 200px;

  width: var(--w);
  aspect-ratio: 1;
  position: relative;
  display: inline-grid;
  margin: 30px;
  padding-top: 20px;
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
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

  inset: 0;
  background: radial-gradient(farthest-side, var(--c) 98%, #0000) top/var(--b)
      var(--b) no-repeat,
    conic-gradient(var(--c) calc(var(--p) * 1%), #0000 0);
  /* -webkit-mask: radial-gradient(
    farthest-side,
    #0000 calc(99% - var(--b)),
    #000 calc(100% - var(--b))
  ); */
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
/* logo */
#logo {
  width: 30%;
}
/* elke paragraaf neemt 20px margin, dan ziet het er mooier uit */
p {
  margin: 20px;
}
</style>
