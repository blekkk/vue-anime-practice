<template>
  <div class="anime">
    <h3>{{ anime.title }}</h3>
    <img :src="anime.image_url" :alt="anime.title" />
  </div>
</template>



<script>
export default {
  name: "Anime",
  props: {
    anime: Object,
  },
  methods: {
    titleClick(mal_id) {
      alert(mal_id);
    },
  },
};
</script>



<style>
.anime {
  box-shadow: 0 0 3px #ccc;
  padding: 1rem;
}

.anime h3:hover {
  text-decoration: underline;
  cursor: pointer;
}
</style>