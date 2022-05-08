<template>
  <div>
    <div class="d-inline-flex flex-wrap justify-content-center">
    <div class="card m-4 shadow p-3 mb-5 bg-body rounded text-center" style="width: 15rem;" v-for="listChapter in surah" :key="listChapter.id">
      <div class="card-body ">
        <h6 class="card-title">{{ listChapter.name_simple }}</h6>
        <p class="card-text fw-lighter ">{{listChapter.revelation_place}} <br>{{listChapter.verses_count}} ayat</p>
        <!-- <p class="card-text fw-lighter"></p> -->
        <router-link :to="{name: 'surah', params: {id:listChapter.id} }" class="btn btn-primary">Baca Surah</router-link>
      </div>
    </div>
  </div>
  </div>
</template>
<script>
import axios from 'axios'
import { ref } from 'vue'
const urlSurah = 'https://api.quran.com/api/v4/chapters?language=id'
export default {
  data() {
    return {
      surah: ref([])
    }
  },
  mounted() {
    this.getSurah()
  },
  methods: {
    getSurah() {
      axios.get(urlSurah)
        .then((response) => {
          this.surah = response.data.chapters
        }).catch((error) => {
          console.log('error' + error);
        })
    }
  }
}
</script>