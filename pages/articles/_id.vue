<template>
  <article class="article">
    <div class="single">
      <h1 class="article-title">{{ article.fields.title }}</h1>
      <p class="article-created-at">{{ formatDate(article.sys.createdAt) }}</p>
      <p class="article-content" v-html="$md.render(article.fields.content.content[0].content[0].value)"></p>
    </div>
  </article>
</template>

<script>
import client from '~/plugins/contentful'

export default {
  asyncData({ params, error, payload }) {
    if (payload) return { article: payload }
    return client
      .getEntries({
        content_type: 'article',
        'fields.id': params.id,
      })
      .then(entries => {
        return { article: entries.items[0] }
      })
      .catch(e => console.log(e))
  },
  head() {
    return {
      title: this.article.fields.title,
    }
  },
  mounted() {
    console.log(this.article)
  },
  methods: {
    formatDate(iso) {
      const date = new Date(iso)
      const yyyy = new String(date.getFullYear())
      const mm = new String(date.getMonth() + 1).padStart(2, "0")
      const dd = new String(date.getDate()).padStart(2, "0")
      return `${yyyy}.${mm}.${dd}`
    }
  }
}
</script>

<style lang="scss">
article.article {
  padding: 10px;
  .single {
    max-width: 900px;
    margin: 0 auto;
    padding: 10px;
    color: #222;
    border: 2px solid #444;
    border-radius: 10px;
    h1, h2, h3 {
      margin: 16px 0;
    }
    h1.article-title {
      font-size: 32px;
      text-decoration: underline;
    }
    .article-content {
      h1 {
        font-size: 32px;
      }
      h2 {
        font-size: 24px;
        background: #ccc
      }
      p {
        margin: 16px 0;
        font-size: 16px;
      }
      img {
        max-width: 100%;
        border: 1px solid #000;
      }
    }
  }
}
</style>