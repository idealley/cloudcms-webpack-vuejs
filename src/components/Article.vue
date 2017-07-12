<template>
  <div class="article">
    <breadcrumb :breadcrumb="breadcrumb"></breadcrumb>
    <h1>{{article.title}}</h1>
    <p>{{article.body}}</p>
  </div>
</template>

<script>
import axios from 'axios'

import Breadcrumb from './Breadcrumb'

export default {
  name: 'article',
  components: {
    breadcrumb: Breadcrumb
  },

  data () {
    return {
      article: {},
      breadcrumb: {}
    }
  },

  // Fire a request when the component is created.
  created () {
    this.fetchData()
  },

  watch: {
    '$route': 'fetchData'
  },

  methods: {
    fetchData () {
      this.error = this.post = null
      this.loading = false
      const slug = this.$route.params.slug

      axios.get(`http://localhost:3000/${slug}`)
      .then(response => {
        this.article = response.data.item[0]
        this.breadcrumb = response.data.breadcrumb
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

.links > li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
