<template>
  <div class="countries-list-container">
    <div class="filtros">
      <input class="input-country" type="text" placeholder="Search your country" v-model="nombrePais">
      <select class="input-region" id="input-region" v-model="filtroPais">
        <option class="region-option" value="">All</option>
        <option class="region-option" value="Europe">Europe</option>
        <option class="region-option" value="Asia">Asia</option>
        <option class="region-option" value="Africa">Africa</option>
        <option class="region-option" value="Oceania">Oceania</option>
        <option class="region-option" value="Americas">Americas</option>
      </select>
    </div>
    <div class="pais" v-for="names of countriesInfo" v-bind:key="names" @click="alertar(names.alpha2Code)" v-show="names.name.includes(nombrePais) && names.region.includes(filtroPais)">
      <div class="img-paises">
        <img v-bind:src="names.flag" alt="Country FLag" />
      </div>
      <div class="pais--info" @click="alerta(names.name)">
        <h3>{{ names.name }}</h3>
        <p><b>Population:</b> {{ names.population }}</p>
        <p><b>Region:</b> {{ names.region }}</p>
        <p><b>Capital:</b> {{ names.capital }}</p>
      </div>
    </div>
  </div>
  
</template>
<script>
export default {
  data() {
    return {
      countriesInfo: [],
      nombrePais: '',
      filtroPais: ''
    };
  },
  mounted() {
    this.axios({
      method: "GET",
      url: "https://restcountries.com/v2/all",
    })
      .then((res) => {
        this.countriesInfo = res.data;
        console.log(this.countriesInfo[0]);
      })
      .catch((err) => {
        console.log(err);
      });
      /*SELECT*/
      
      
  },
  methods:{
      alertar(id){
          window.location.href = `/country/${id}`;
      }
  }
};
</script>
<style>
.countries-list-container {
  margin-top: 20px;
  row-gap: 40px;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.pais {
  border: 1px solid #dfdfdf;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  min-width: 250px;
  max-width: 250px;
  height: 380px;
  background-color: #fff;
}
@media (max-width: 570px){
    .pais{
      margin: 0 auto;
    }
}
.pais:hover {
  cursor: pointer;
  border: none;
  box-shadow: 1px 1px 5px -1px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 1px 1px 5px -1px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 1px 1px 5px -1px rgba(0, 0, 0, 0.75);
}
.pais--info {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 10px;
  /* background-color: red; */
  height: 150px;
}
.pais img {
  width: 100%;
  max-height: 180px;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
}
.img-paises {
  height: 180px;
}
.pais h3 {
  font-size: 25px;
}
.filtros{
  width: 100%;
  display: flex;
  justify-content: space-between;
}
.input-country,
.input-region,
.input-country:focus,
.input-region:focus{
  height: 4rem;
  box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
  padding-left: 1rem;
  border: none;
  outline: none;
}
.input-country{
  width: 70%;
  max-width: 50rem;
  
}
.input-region{
  width: 25%;
  max-width: 20rem;
  border: none;
}

</style>