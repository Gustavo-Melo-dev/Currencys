<template>
<div class="container grid-lg py-2 my-2">
    <div class="card">
        <div class="card-header">
            <div class="h4 text-center text-bold py-2">All Currencys</div>
        </div>
        <div class="card-body">
            <ListQuotes />
        </div>
    </div>
</div>
</template>

<script>
import ListQuotes from '../components/ListQuotes.vue'

export default {
    name: "Dashboard",
    components: {  ListQuotes  },
    setup() {
        
    }
}
</script>

<style>

</style>