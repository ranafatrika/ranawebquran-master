<script>
import { ref } from "vue";
import axios from "axios";
import NavBar from "../components/navbar.vue";

export default {
  components: { NavBar },
  data()
  {
    return {
      error: false,
      loading: true,
      juz: ref([]),
      isijuz: ref([]),
    }
  },
  watch:{
    $route(){
      this.getJuz();
      this.getIsiJuz();
    }
  },

  mounted()
  {
    this.getJuz()
    this.getIsiJuz()
  },

  methods: {
    getJuz()
    {
      axios.get('https://api.quran.com/api/v4/juzs/' + this.$route.params.id)
        .then(response =>
        {
          this.juz = response.data.juz;

        })
        .catch(error =>
        {
          console.log(error)
          this.error = true
        })
        .finally(() => this.loading = false)
    },
    getIsiJuz()
    {
      axios.get('https://api.quran.com/api/v4/quran/verses/uthmani?juz_number=' + this.$route.params.id)
        .then(response =>
        {
          this.isijuz = response.data.verses;
        })
        .catch(error =>
        {
          console.log(error)
          this.error = true
        })
        .finally(() => this.loading = false)
    },

  }
}
</script>

<template>
  <NavBar/>
  <div class="text-center mt-5">
    <h2>Juz {{ $route.params.id }}</h2>
    <h4 v-for="quran in isijuz" :key="quran.id" class="text-lg-end mt-5">
      {{ quran.text_uthmani }} {{quran.verse_key}}
    </h4>
  </div>
</template>
<style>
.text-center{
  font-family: fontArab;
}
</style>