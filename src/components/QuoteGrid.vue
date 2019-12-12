<template>
  <div class="row">
    <quote v-for="(q, idx) in quotes" v-bind:key="q" @click.native="deleteQuote(idx)" >
    {{ q }}
    </quote>
  </div>
</template>

<script>
import Quote from './Quote.vue'
export default {
  props: ['quotes'],
  components: {
    quote: Quote,
  },
  methods: {
    deleteQuote(idx) {
      this.$emit('deltedQuoteId', idx)
    }
  }
}
</script>

<style scoped>

</style>
