<template>
  <section class="latest-articles">
    <div class="articles">
      <nuxt-link :to="'articles/'+article.fields.id" class="article" v-for="(article, index) in articles" :key="index">
        <div class="article-text">
          <p>{{ formatDate(article.sys.createdAt) }}</p>
          <h2>{{ article.fields.title }}</h2>
        </div>
      </nuxt-link>
    </div>
  </section>
</template>

<script>
import client from '~/plugins/contentful'

export default {
  asyncData({ params }) {
    return client
      .getEntries({
        content_type: 'article',
        order: '-sys.createdAt',
      })
      .then(entries => {
        return { articles: entries.items }
      })
      .catch(e => console.log(e))
  },
  head: {
    title: '記事一覧',
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
section.latest-articles {
  padding: 10px;
  .articles {
    max-width: 900px;
    margin: 0 auto;
    padding: 10px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    background: #ddd;
    a.article {
      width: calc(100% / 2 - 20px);
      @media (min-width: (768px)) {
        width: calc(100% / 3 - 20px);
      }
      margin: 10px;
      background: #fff;
      text-decoration: none;
      color: #111;
      .thumb {
        width: 100%;
        padding-bottom: 75%;
        position: relative;
        overflow: hidden;
        img {
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          max-width: 100%;
        }
      }
      .article-text {
        padding: 5px 10px 10px;
        h2 {
          width: fit-content;
          font-size: 20px;
        }
      }
    }
  }
}
</style>