<template>
    <div class="countries-container">
        <CountriesList/>
    </div>
</template>

<script>
import CountriesList from '../components/CountriesList.vue'

export default {
    data(){
        return{
        }
    },
    components:{
        CountriesList
    }
}
</script>

<style>
.countries-container{
    width: 90%;
    margin: 0 auto;
    background-color: rgba(255, 255, 255, 0);
}
</style>