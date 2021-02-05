<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <div class="d-flex flex-wrap justify-content-center">
                    <Card v-for="(pokemon, index) in pokemons"
                    :key="index" :name="pokemon.name" :text="pokemon.url" />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import Card from "./../components/Card.vue";
    export default {
        name: 'Pokemons',
        components: {
            Card
        },
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
