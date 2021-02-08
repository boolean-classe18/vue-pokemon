<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <Form @newSearch="searchPokemon" @resetSearch="showAll" />
                <div class="d-flex flex-wrap justify-content-center" v-if="showSinglePokemon">
                    <Single :name="singlePokemon.name"
                    :type="singlePokemon.types[0].type.name"
                    :image="singlePokemon.sprites.other.dream_world.front_default" />
                </div>
                <div class="d-flex flex-wrap justify-content-center" v-else>
                    <Card v-for="(pokemon, index) in pokemons"
                    :key="index" :name="pokemon.name" :text="pokemon.url" />
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import Card from "./../components/Card.vue";
    import Form from "./../components/Form.vue";
    import Single from "./../components/Single";
    export default {
        name: 'Pokemons',
        components: {
            Card,
            Form,
            Single
        },
        data() {
            return {
                pokemons: [],
                singlePokemon: {},
                showSinglePokemon: false
            }
        },
        mounted() {
            const self = this;
            this.axios.get(this.base_url + 'pokemon').then(response => {
                console.log(response.data.results);
                self.pokemons = response.data.results;
            });
        },
        methods: {
            searchPokemon(name) {
                const self = this;
                this.axios.get(this.base_url + 'pokemon/' + name).then(response => {
                    self.singlePokemon = response.data;
                    self.showSinglePokemon = true;
                });
            },
            showAll() {
                this.showSinglePokemon = false;
            }
        }
    }
</script>
