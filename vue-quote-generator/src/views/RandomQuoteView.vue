<template>
    <h1>Random Quote</h1>
    <p v-if="loading">Loading...</p>
    <p v-else>"{{ quote }}"</p>
    <p class="author">— {{ author }}</p>
    <div class="buttons">
        <button @click="getQuote">Get New Quote</button>
        <GoBack />
    </div>
</template>

<script>

import GoBack from '../components/GoBack.vue'
import axios from 'axios'

export default {
  
    components: {
    GoBack
  },

  data() {
    return {
      quote: '',
      author: '',
      loading: false
    }
  },
  methods: {
    async getQuote() {
      this.loading = true
      try {
        const response = await axios.get('https://quotes15.p.rapidapi.com/quotes/random/?language_code=en', {
          headers: {
            'x-rapidapi-host': 'quotes15.p.rapidapi.com',
            'x-rapidapi-key': '31f1d19a76msh2f8831495d6a964p174655jsnae65cc16629b'
          }
        })
        this.quote = response.data.content
        this.author = response.data.originator.name
      } catch (error) {
        console.error('Error fetching quote:', error)
        this.quote = 'Oops! Something went wrong.'
        this.author = ''
      } finally {
        this.loading = false
      }
    }
  },
  mounted() {
    this.getQuote()
  }
}
</script>