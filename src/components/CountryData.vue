<template >
  <div>
    <div id="search-container">
      <input id="search" v-model="search" placeholder="Search Country">
    </div>
      
       <div class="country-data ">
        <div class="country-row row" v-for="(country,index) in searchCountry" :key="index">
             <div class="flag col-3"><img :src="country.countryInfo.flag" :alt="country.country"></div>
             <div class="country-info col-9">
                <div class="country-name">{{ numberWithCommas(country.country) }}</div>
                <div class="country-cases row">
                    <div class="case-stats col-6">
                      <p class="headings"> Total Cases</p>
                      <p class="cases">{{ numberWithCommas(country.cases) }}</p>
                    </div>
                     <div class="case-stats col-6">
                      <p class="headings"> Today's Cases</p>
                      <p class="cases">{{ numberWithCommas(country.todayCases) }}</p>
                    </div>
                     <div class="case-stats col-6">
                      <p class="headings"> Total Deaths</p>
                      <p class="deaths">{{ numberWithCommas(country.deaths) }}</p>
                    </div>
                     <div class="case-stats col-6">
                      <p class="headings" > Today's Deaths</p>
                      <p class="deaths">{{ numberWithCommas(country.todayDeaths) }}</p>
                    </div>
                     <div class="case-stats col-6">
                      <p class="headings"> Total Recovered</p>
                      <p class="recovery">{{ numberWithCommas(country.recovered) }}</p>
                    </div>
                    <div class="case-stats col-6">
                      <p class="headings"> Today's Recovery</p>
                      <p class="recovery">{{ numberWithCommas(country.todayRecovered) }}</p>
                    </div>
                </div>
             </div>  
        </div>
    </div>
  </div>
   
</template>

<script>

export default {
  name: 'CountryData',
  props: ['countryDetails'],
 
 data () {
    return {
       search: '',
    }
  },
  methods: {
    numberWithCommas(x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    } 
  } ,
  computed: {
    searchCountry() {
      let searchedCountry = this.countryDetails

      if(this.search) {
          searchedCountry = searchedCountry.filter((country) => {
            return country.country
            .toUpperCase()
            .includes(this.search.toUpperCase())
          })
      } 
      console.log(this.search)
      console.log(searchedCountry)
      return searchedCountry
    }
  }
}

</script>

<style scoped>
/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey; 
  border-radius: 10px;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: gray; 
  border-radius: 7px;
}

p {
  font-size: 14px;
  margin: 0;
}
</style>


