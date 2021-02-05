<template>
    <div>
        <ul>
            <li v-for="(pokemon, index) in pokemons" :key="index">
                {{ pokemon.name }}
            </li>
        </ul>
    </div>
</template>
<script>
    export default {
        name: 'Pokemons',
        data() {
            return {
                pokemons: []
            }
        },
        mounted() {
            const self = this;
            this.axios.get(this.base_url + 'pokemon').then(response => {
                console.log(response.data.results);
                self.pokemons = response.data.results;
            });
        }
    }
</script>
