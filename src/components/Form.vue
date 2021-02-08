<template>
    <form @submit.prevent="search"
    class="form-inline d-flex justify-content-center mb-2">
        <input type="text" placeholder="cerca un pokemon"
        class="form-control" v-model="searchText">
        <input type="submit" value="Cerca" class="btn btn-primary ml-2">
        <input type="reset" value="Cancella filtro" class="btn btn-secondary ml-2" @click="reset">
    </form>
</template>
<script>
    export default {
        name: 'Form',
        data() {
            return {
                searchText: ''
            }
        },
        methods: {
            search() {
                console.log(this.searchText);
                this.$emit('newSearch', this.searchText);
            },
            reset() {
                console.log('cliccato su reset');
                this.searchText = '';
                this.$emit('resetSearch');
            }
        }
    }
</script>
