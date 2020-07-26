<template>
    <div id="body">
        <!-- Select -->
        <div id="chooseCountry">
            <p id="label"> Select a Country </p>
            <select align=center v-model="selected" @change="changeCountry($event)">
                <option disabled value=""> Which country? </option>
                <option :selected="true" v-for="name in namesCountries" :key="name" :value="name">
                    {{ name }}
                </option>
            </select>
        </div>

        <!-- Card -->
        <div class="card" v-show="c.nativeName">
            <div class="card-content">
                <div class="media">
                <div class="media-left">
                    <figure class="image is-96x96" v-on:click="modalImage = true">
                        <img :src='c.flag' alt="Flag">
                    </figure>
                </div>
                <div class="media-content">
                    <p class="title is-4">{{c.name}}</p>
                    <p class="subtitle is-6">{{c.nativeName}}</p>
                </div>
                </div>

                <div class="content">
                    <Table :countryInfo=c />
                </div>
            </div>
        </div>

        <pre>
            {{c.text}}
        </pre>
        
        <div id="modal-ter" class="modal is-active" v-show="modalImage" v-on:click="modalImage = false">
            <div class="modal-background"></div>
            <div class="modal-content">
                <p class="image is-4by3">
                <img :src="c.flag" alt="">
                </p>
            </div>
            <button class="modal-close is-large" aria-label="close"></button>
        </div>

    </div>
</template> 

<script>
    import countries from '../assets/countries';
    import Table from './Table.vue'

    export default {
        data() {
            return {
                selected:"Choose a country",
                selectedCountry: undefined,
                countries,
                c: {
                    name: undefined,
                    capital: undefined,
                    region: undefined,
                    subregion: undefined,
                    population: undefined,
                    nativeName: undefined,
                    currencies: undefined,
                    languages: undefined,
                    flag: undefined
                },
                modalImage: false
            }
        },
        methods:{
            async changeCountry(event){
                this.selectedCountry = event.target.value;
                var foundCountry = countries.find(c => c.name === event.target.value);

                var langs = []; var currencies = []
                foundCountry.languages.forEach(l=>{
                    langs.push(l.name)
                });
                foundCountry.currencies.forEach(cur=> currencies.push(cur.name))

                this.c = {
                    name: foundCountry.name,
                    capital: foundCountry.capital,
                    region: foundCountry.region,
                    subregion: foundCountry.subregion,
                    population: foundCountry.population,
                    nativeName: foundCountry.nativeName,
                    currencies: currencies.join(),
                    languages: langs.join(),
                    flag: foundCountry.flag
                }
            },

            viewFlag(event){
                console.log(event.target.value)
                this.modalImage = true;
            }
        },
        computed: {
            namesCountries: () => {
                var namesCountries = []
                countries.forEach(country=>{
                    namesCountries.push(country.name)
                })
                return namesCountries
            },
        },

        components: {
            Table
        }
    }
</script>

<style scoped>
    #body{
        margin: auto;
        width: 70%;
        padding: 10px;
    }

    .card{
        margin-bottom: 200px;
    }

    #chooseCountry{
        font-size:16px;
        color: black;
        text-align: center;
        margin-bottom: 20px;
        margin-top: 10px;
    }

    select, option{
        text-align:center;
        margin: auto;
        font-size: 20px;
    }
</style>