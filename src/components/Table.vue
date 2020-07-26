<template>
        <table>
            <tr v-show='countryInfo.capital'>
                <th class="title">  Capital: </th>
                <th> {{countryInfo.capital}} </th>
            </tr>
            <tr v-show='countryInfo.region'>
                <th class="title"> Region: </th>
                <th> {{countryInfo.region}} </th>
            </tr>
            <tr v-show='countryInfo.subregion'>
                <th class="title"> Subregion: </th>
                <th> {{countryInfo.subregion}} </th>
            </tr>
            <tr v-show='countryInfo.currencies'> 
                <th class="title"> Currencies: </th>
                <th> {{`${countryInfo.currencies}`}} </th>
            </tr>
            <tr v-show='countryInfo.languages'>
                 <th class="title"> Languages: </th>
                 <th> {{countryInfo.languages}} </th>
            </tr>
        </table>
</template>

<script>
export default {
    props: {
        countryInfo: Object
    }
}
</script>

<style scoped>

    table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        margin: auto;
        width: 30%;
        padding: 10px;
    }

    td, th {
        text-align: left;
        padding: 8px;
        font-size: 15px;
        width: 40%;
    }
    
    th.title{
        width: 10%;
        text-align: left;
        padding: 8px;
        font-size: 20px;
    }

</style>