<template>
    <div>
        <h1>Country List</h1>
        <ul>
            <li v-for="country in countries" :key="country.id">
                <a href="#" @click.prevent="showCountryDetails(country)">{{ country.name }}</a>
            </li>
        </ul>
    </div>
    <div>
        <CountryDetails v-if="selectedCountry" :country="selectedCountry" @kill="hideCountryDetails"/>
    </div>
</template>

<script>
import CountryDataService from "@/service/CountryDataService";
import CountryDetails from "./CountryDetails.vue";

export default {
    data() {
        return {
            countries: [
                // {id:1, name:"United States" ,population:331142779},
                // {id:2, name:"Spain", population:47450795},
                // {id:3, name:"Japan", population:125570000}
            ],
            selectedCountry: null,
        }
    },
    components: {
        CountryDetails
    },
    created() {
        this.fetchCountries()
    },
    methods: {
        fetchCountries() {
            CountryDataService.getCountries() 
                .then(response => {
                    this.countries = response.data
                })
                .catch(error => {
                    console.error('Error teching countries: ', error);
                })
        },
        showCountryDetails(country) {
            this.selectedCountry = country;
        },
        hideCountryDetails() {
            this.selectedCountry = null;
        }
    }
}
</script>

<style>
</style>