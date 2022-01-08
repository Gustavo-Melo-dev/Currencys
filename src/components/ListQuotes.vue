<template>
  <div class="table">
    <thead>
        <tr>
            <th>Code:</th>
            <th>Name:</th>
            <th>Max:</th>
            <th>Min:</th>
            <th>Variation:</th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr v-for="(quote, index) in quotes" :key="index">
            <td>{{ index }}</td>
            <td>{{ quote.name }}</td>
            <td>{{ quote.high }}</td>
            <td>{{ quote.low }}</td>
            <td>
                <span 
                class="label label-rounded text-small"
                :class="{ 'label-error': quote.pctChange < 0, 'label-success': quote.pctChange > 0}">
                    {{ quote.pctChange }} %
                </span>
            </td>
            <td></td>
        </tr>
    </tbody>
  </div>
</template>

<script>
import axios from 'axios'
import { reactive, toRefs } from '@vue/reactivity'
import { onMounted } from '@vue/runtime-core'

export default {
    name: "ListQuotes",
    setup() {
        const state = reactive({
            quotes: {}
        })

        onMounted(() => {
        axios.get("https://economia.awesomeapi.com.br/last/USD-BRL,EUR-BRL,BTC-BRL").then((response) => {
            state.quotes = response.data
        })
        })

         return {
        ...toRefs(state)
        }
    }
}
</script>

<style>

</style>