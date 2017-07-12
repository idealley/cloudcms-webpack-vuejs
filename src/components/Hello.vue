<template>
  <div class="hello">
    <h1>News</h1>
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
      <ul v-if="posts && posts.length">
        <li v-for="post of posts">
          <p><strong>{{post.title}}</strong></p>
          <p v-html="post.leadParagraph"></p>
          <a :href="post.url">More...</a>
        </li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'hello',
  data () {
    return {
      posts: [],
      errors: []
    }
  },

  // Fire a request when the component is created.
  created () {
    axios.get(`https://api.ersnet.org/news`)
    .then(response => {
      console.log(response)
      this.posts = response.data.data
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

a {
  color: #42b983;
}
</style>
