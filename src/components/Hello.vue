<template>
  <div class="hello">
    <h1>{{category.title}}</h1>
    <h2>Essential Links</h2>
    <ul class="links">
      <li><a href="https://www.cloudcms.com/" target="_blank">Cloud CMS</a></li>
      <li><a href="https://www.cloudcms.com/documentation.html" target="_blank">Cloud CMS - Documentation</a></li>
      <li><a href="https://github.com/gitana" target="_blank">Cloud CMS - Github</a></li>
      <li><a href="https://vuejs.org" target="_blank">Vue</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
      <li><a href="https://laracasts.com/series/learn-vue-2-step-by-step" target="_blank">Laracast (Vuecast) - Getting started with Vue</a></li>
    </ul>
    <breadcrumb :breadcrumb="breadcrumb"></breadcrumb>
    <p>{{category.body}}</p>  
    <ul v-if="posts && posts.length">
      <li v-for="post of posts">
        <p><strong>{{post.title}}</strong></p>
        <p v-html="post.leadParagraph"></p>
        <router-link :to="`/${post.slug}`">More...</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

import Breadcrumb from './Breadcrumb'

export default {
  name: 'hello',
  components: {
    breadcrumb: Breadcrumb
  },

  data () {
    return {
      category: {},
      breadcrumb: {},
      posts: [],
      errors: []
    }
  },

  // Fire a request when the component is created.
  created () {
    axios.get(`http://localhost:3000/a-category`)
    .then(response => {
      this.posts = response.data.items
      this.breadcrumb = response.data.breadcrumb
      this.category = response.data.item[0]
    })
    .catch(e => {
      this.errors.push(e)
    })
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

.breadcrumb > li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
