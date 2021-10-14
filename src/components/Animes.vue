<template>
  <h2>Anime List</h2>
  <form @submit.prevent="getSeasonalData">
    <span>Input a year and select a season:</span>
    <input type="number" v-model="formInput.year" required>
    <select v-model="formInput.season" required>
      <option value="winter">Winter</option>
      <option value="spring">Spring</option>
      <option value="summer">Summer</option>
      <option value="fall">Fall</option>
    </select>
    <button type="submit">Ok</button>
  </form>
  <br>
  <p>{{ loading }}</p>
  <div class="animes">
    <Anime v-for="anime in animes" :key="anime.mal_id" :anime="anime" />
  </div>
</template>



<script>
import axios from "axios";
import Anime from "./Anime.vue";

export default {
  name: "Animes",
  components: {
    Anime,
  },
  data() {
    return {
      animes: [],
      formInput: {
        year: 2021,
        season: 'summer'
      },
      loading: '',
    };
  },
  methods: {
    async getSeasonalData () {
      const baseURL = "https://api.jikan.moe/v3/season";
      this.loading = 'Loading, please wait...';

      const result = await axios.get(`${baseURL}/${this.formInput.year}/${this.formInput.season}`);
      this.animes = result.data.anime;
      this.loading = '';
    }
  },
  watch: {
    formInput: {
      handler(val) {
        console.log(JSON.stringify(val));
      },
      deep: true
    }
  },
  created: async function () {
    this.getSeasonalData();
  },
};
</script>



<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: var(--main-color);
}
.animes {
  display: grid;
  grid-template-columns: auto auto auto;
  column-gap: 8px;
  row-gap: 8px;
}
.anime {
  box-shadow: 0 0 3px #ccc;
}
</style>
