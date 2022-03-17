<template>
    <div class="country-info-container">
        <button @click="irAHome()">
            <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-chevron-left" width="20" height="20" viewBox="0 0 24 24" stroke-width="1" stroke="#000000" fill="none" stroke-linecap="round" stroke-linejoin="round">
                <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                <polyline points="15 6 9 12 15 18" />
            </svg>
            <p class="back">
                Back
            </p>
            <span style="width:10px"></span>
        </button>
        <h2 class="country-name--title">{{countryInfo.name}}</h2>
        <div class="country-info">
            <div>
                <img class="country-info--img" :src="countryInfo.flag" alt="Imagen Pais">
            </div>
            <div class="country-info--txt">
                <p><b>Native Name:</b> {{countryInfo.nativeName}}</p>
                <p><b>Capital:</b> {{countryInfo.capital}}</p>
                <p><b>Region:</b> {{countryInfo.region}}</p>
                <p><b>Subregion:</b> {{countryInfo.subregion}}</p>
                <p><b>Population:</b> {{countryInfo.population}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
           id:  this.$route.params.id,
           countryInfo: []
        }
    },
    mounted(){
        this.axios({
            method:'GET',
            url:`https://restcountries.com/v2/alpha/${this.id}`
        }).then(res=>{
            this.countryInfo = res.data
            console.log(this.countryInfo);
        }).catch(err=>{
            console.log(err);
        })
    },
    methods:{
        irAHome(){
             window.location.href = `/`;
        }
    }
}
</script>

<style>
.country-info-container{
    /* background-color: red; */
    width: 90%;
    margin: 0 auto;
}
.country-name--title{
    text-align: center;
    padding: 0 0 50px 0;
    font-size: 30px;
    text-transform: uppercase;
}
.country-info{
    display: grid;
    grid-template-columns: 1fr;
}
@media (min-width: 992px){
    .country-info{
        grid-template-columns: 2fr 3fr;
    }
}
.country-info img{
    width: 100%;
    padding: 10px;
}
.country-info--txt{
    padding: 10px 0 0 100px;
}
.country-info--txt p{
    margin-bottom: 20px;
}
button{
    display: flex;
    background-color: #fff;
    align-items: center;
    width: 100px;
    height: 40px;
    border: none;
    justify-content: space-evenly;
    margin-left: 10px;
    box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
    -webkit-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
    margin-top: 5rem;
}
button:hover{
    cursor: pointer;
    background-color: rgb(245, 245, 245);
}
button:active{
    box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 1px 1px 2px -1px rgba(0, 0, 0, 0.75);
    background-color: rgb(201, 201, 201);
}
</style>