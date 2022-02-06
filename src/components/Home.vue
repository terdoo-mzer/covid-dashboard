<template>
<main class="row">
  <div class="col-sm-5"> <CountryData :countryDetails="CountryStats" /></div>
  <div class="col-sm-7"><GlobalData :globaData="globData" /></div>
</main>
</template>

<script>
import GlobalData from '@/components/GlobalData.vue'
import CountryData from '@/components/CountryData.vue'

export default {
  name: 'Home',
    components: {
      GlobalData,
      CountryData
  },
 data () {
    return {
      globData: {},
      CountryStats: [],
      apiUrls: ['https://disease.sh/v3/covid-19/all',
              'https://disease.sh/v3/covid-19/countries'
      ]
    }
  },
  methods: {
     async fetchCovidData() {  
      try{
         // Request multiple endpoints using Promise.all()
        const response = await Promise.all(this.apiUrls.map(url => fetch(url)
        .then(res => res.json())))
        return response
      } catch(e) {
          console.log("Error", e)
      }
    }
  },
  async created() {
     const data = await this.fetchCovidData()
     const globalData = data.at(0)
     const countryData = data.at(1)
     this.globData = globalData
     this.CountryStats = countryData
  },
} 
</script>


