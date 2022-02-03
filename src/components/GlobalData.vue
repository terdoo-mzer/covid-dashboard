<template>
  <div >
      <h3>{{ title }}</h3>

      <!-- Row 1 -->
      <div class="container">
        <div class="row mb-4 global-stats">
          <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
              <p class="headings">World Population:</p>
              <p class="font-weight-bold">{{ numberWithCommas(globaData.population) }}</p>
          </div>
          <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
              <p class="headings">Affected Countries:</p>
              <p class="cases font-weight-bold">{{ numberWithCommas(globaData.affectedCountries) }}</p>
          </div>
          <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
               <p class="headings">Total Cases:</p>
               <p class="cases font-weight-bold">{{ numberWithCommas(globaData.cases) }}</p>
          </div>
          <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
                <p class="headings">Today's Cases:</p>
                 <p class="cases">{{ numberWithCommas(globaData.todayCases) }}</p>
          </div>
       </div>
      </div>
   

      <!-- Row 2 -->
    
      <div class="container">
        <div class="row global-stats">
            <div class="global-stat col-lg col-md-6 col-sm-6 mb-4"> 
                    <p class="headings">Total Deaths:</p> 
                    <p class="deaths">{{ numberWithCommas(globaData.deaths) }}</p>
            </div>
            <div class="global-stat col-lg col-md-6 col-sm-6 mb-4"> 
                    <p class="headings">Today's Deaths:</p> 
                    <p class="deaths">{{ numberWithCommas(globaData.todayDeaths) }}</p>
            </div>
            <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
                    <p class="headings">Total Recovery:</p>
                    <p class="recovery">{{ numberWithCommas(globaData.recovered) }}</p>
            </div>
            <div class="global-stat col-lg col-md-6 col-sm-6 mb-4">
                <p class="headings">Today's Recovery:</p>
                <p class="recovery">{{ numberWithCommas(globaData.todayRecovered) }}</p>
            </div>
        </div>
      </div>
    
  </div>
</template>

<script>
export default {
    props: ['globaData'],
    name: 'GlobalData',
    data() {
        return {
            title: 'Global Data'
        }
    },
    methods: {
         numberWithCommas(x) {
             return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    }
}
</script>

<style scoped>
    p {
        margin: 0;
    }
   @media only screen and(max-width: 576px) {
        .global-stats {
            display: grid !important;
            grid-template-columns: 1fr 1fr !important;
        }
    }
</style>