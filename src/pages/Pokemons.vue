<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <div class="d-flex flex-wrap justify-content-center">
                    <div class="card m-2"
                    style="width: 18rem;"
                    v-for="(pokemon, index) in pokemons" :key="index">
                        <div class="card-body">
                            <h5 class="card-title">
                                {{ pokemon.name }}
                            </h5>
                            <p>
                                {{ pokemon.url }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

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
