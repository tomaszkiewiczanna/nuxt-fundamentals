<template>
  <section>
    <article>
      <h2>{{post.title}}</h2>
      <span>{{post.content}}</span>
    </article>
    <h2>Polecamy przecyztać także:</h2>
    <ul>
      <li v-for="item in relatedPosts" :key="item.id">
        <nuxt-link :to="`/posts/${item.id}`">{{item.title}}</nuxt-link>
        </li>
    </ul>
  </section>
</template>
<script lang="ts">
export default {
  data() {
    return {
      id: this.$route.params.id,
      posts: [
        {
          id: "piesek",
          title: "piesek - lubi szczekać i rzucać piłkę",
          content: "dxidjci whuc yw cycicusi us hdcus cdhus hcu"
        },
        {
          id: "pingwin",
          title: "pingwin - zabawny ptak",
          content: "biało czarny garnitur i rybka na kolacje"
        },
        {
          id: "malpka",
          title: "małpka - zabawny ssak",
          content: "bliski krewny człowieka"
        }
      ]
    };
  },
  head () {
    return {
      title : this.post.title,
      meta: [
        {name: 'twitter:title', content: this.post.title},
        {name: 'twitter:description', cotnet: this.post.content}
    ]
    }
  },
  computed: {
    post() {
      return this.posts.find(post => post.id === this.id);
    },
    relatedPosts() {
      return this.posts.filter(post => post.id !== this.id);
    }
  }
};
</script>
