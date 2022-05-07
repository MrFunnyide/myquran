<template>
     <div class="m-3">
          <ol>
               <li v-for="ayat in ayatQuran" :key="ayat.id" style="list-style: none;">
                    <p class="ayat">{{ ayat.text_uthmani }}<sub>({{ayat.verse_key}})</sub> </p> <hr>
               </li>
          </ol>
     </div>
</template>
<script>
import axios from 'axios'
import { ref } from 'vue'
export default {
     data() {
          return {
               ayatQuran: ref([]),
               translateQuran: ref([])
          }
     },
     mounted() {
          this.getAyatQuran()
          this.getTranslateQuran()
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
          }
     }
}
</script>
<style>
@import "../styles/app.css";
</style>
