<template>
    <div>
        <div>
            <h1>Country Population</h1>
            <ul>
                <li>Name: {{ country.name }}</li>
                <li>Population: {{ country.population }}</li>
            </ul>
        </div>
        <div>
            <button @click="makeUnseen">Close</button>
        </div>
    </div>  
</template>

<script>
export default {
    props: ['country'],
    methods: {
        makeUnseen() {
            this.$emit('kill')
        }
    }
}
</script>

<style>
</style>