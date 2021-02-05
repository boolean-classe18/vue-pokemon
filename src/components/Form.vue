<template>
    <form @submit.prevent="search"
    class="form-inline d-flex justify-content-center">
        <input type="text" placeholder="cerca un pokemon"
        class="form-control" v-model="searchText">
        <input type="submit" value="Cerca" class="btn btn-primary ml-2">
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
            }
        }
    }
</script>
