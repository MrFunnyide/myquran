<template>
     <div class="jumbotron text-center mt-3">
          <h2>{{infoSurah.name_simple}}</h2>
          <br>
     </div>
     <div>
          <ol>
               <li v-for="(ayat, index) in ayatQuran" :key="index" style="list-style: none;">
                    <p class="ayat m-3"><sub>({{ayat.verse_key}})</sub> {{ ayat.text_uthmani }}</p>
                    <p v-html="translateQuran[index].text"></p>
                    <hr>
               </li>
          </ol>
     </div>
     <p>{{infoSurah.name_simple}}</p>
</template>
<script>
import axios from 'axios'
import { ref } from 'vue'

export default {
     data() {
          return {
               ayatQuran: ref([]),
               translateQuran: ref([]),
               infoSurah: ref([])
          }
     },
     mounted() {
          this.getAyatQuran()
          this.getTranslateQuran()
          this.getInfoSurah()
     },
     methods: {
          getAyatQuran() {
               axios.get(`https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=${this.$route.params.id}`)
               .then((response) => {
                    this.ayatQuran = response.data.verses
               }).catch((error) => {
                    console.log('error' + error)
               })
          },
          getTranslateQuran() {
               axios.get(`https://api.quran.com/api/v4/quran/translations/33?chapter_number=${this.$route.params.id}`)
               .then((response) => {
                    this.translateQuran = response.data.translations
               }).catch((error) => {
                    console.log('error' + error)
               })
          },
          getInfoSurah() {
               axios.get(`https://api.quran.com/api/v4/chapters/${this.$route.params.id}?language=id`)
               .then((response) => {
                    this.infoSurah = response.data.chapter
               }).catch((error) => {
                    console.log('error' + error)
               })
          }
     }
}
</script>
<style>
@import "../styles/app.css";
</style>
